## What is the image?

- Image is the combination of read-only layers stacked in the order they were built (Image is a metadata file indentifying the required layers and explaining how to stack them);
- Image is a **build-time** construct. You can start multiple containers from a single image;
- Image must contains only necessary parts. It can be as slim as possible;
- Image does not contain OS kernel. Usualy it contains OS-related filesystem object;
- Images (layers) are stored in local repository (cache). Usually located in `var/lib/docker/<storage-driver>`).

<img width="369" height="224" alt="image" src="https://github.com/user-attachments/assets/8afd2040-e58b-4eff-a67a-31d680696da3" />

<img width="448" height="247" alt="image" src="https://github.com/user-attachments/assets/18b0d05a-037f-4b3f-9eea-e722febf364f" />

## What is the layer?

Layer is a block of content (e.g. Ubuntu (Layer 1), Node.js (Layer 2), App Code (Layer 3))

<img width="378" height="184" alt="image" src="https://github.com/user-attachments/assets/1233c2da-7bda-4c35-9d77-e991b75c34c4" />

Under the hood, Docker uses `storage drivers` (overlay2 or others) to stack layers and present them as a unified filesystem and image.

Layers can be shared between different images. 

<img width="575" height="331" alt="image" src="https://github.com/user-attachments/assets/85c70afd-92ad-4423-8666-7dba747de66d" />


To inspect layer information:
```sh
docker inspect node:latest
```

<img width="343" height="228" alt="image" src="https://github.com/user-attachments/assets/30fdbb67-8af5-4e59-b46f-e0381f8e0237" />

## Where to store images?

In registries that implement OCI distribution-spec. (Docker Hub)

`Registry -> Repository -> Image`

<img width="412" height="262" alt="image" src="https://github.com/user-attachments/assets/1dda2ae2-6dad-4530-bb21-a7f0dd4ea941" />

## Pulling by digest

Docker uses a **content addresable storage** model where every image gets a cryptographic content hash that we usually cal the **digest**.

- So it's impossible for two different images to have the same digest;
- It's also impossible to change an image without creating a new digest.

To get an image digest before pulling it, use:
1) ```sh
   docker buildx imagetools inspect node:latest
   ```
2) ```sh
   docker pull node:latest@<sha256:digestcode>
   ```

- Images digests are a crypto hash of the image's manifest file (Dockerfile). Each layer gets two hashes:
  1) Content hash (uncompressed)
  2) Distribution hash (compressed) - uses when push/pull to verify no tampering occured.
- Layer digests are a crypto hash of the layer's contents.

## Multi-architecture images

Registry API supports two constructs:
- Manifest lists is a list of architectures supported by an image tag;
- Manifests - lists the layers used to build it.

<img width="641" height="661" alt="image" src="https://github.com/user-attachments/assets/bb028b5f-2df3-4a3c-99b4-c35d4f766e54" />

<img width="446" height="392" alt="image" src="https://github.com/user-attachments/assets/846d4b5a-3fe7-4444-a7e2-3e40f9cb5401" />


Use `docker buildx` command to create multi-architecture images. This command offers two ways to create multi-architecture images:
- Emulation - performs builds for different architectures on local machine by running the build inside a QEMU VM emulating the target architecture;
- Build Cloud - cloud service by Docker Inc., performs build in the cloud on native hardware.
