## What is the image?

Image is a collection of loosely connected read-only layers.
Image is a **build-time** construct. You can start multiple containers from a single image.
Image must contains only necessary parts. It can be as slim as possible.
Image does not contain OS kernel. Usualy it contains OS-related filesystem object.
Images (layers) are stored in local repository (cache). Usually located in `var/lib/docker/<storage-driver>`)
<img width="369" height="224" alt="image" src="https://github.com/user-attachments/assets/8afd2040-e58b-4eff-a67a-31d680696da3" />

<img width="448" height="247" alt="image" src="https://github.com/user-attachments/assets/18b0d05a-037f-4b3f-9eea-e722febf364f" />

## What is the layer?

Layer is a block of content (e.g. Ubuntu (Layer 1), Node.js (Layer 2), App Code (Layer 3))

<img width="378" height="184" alt="image" src="https://github.com/user-attachments/assets/1233c2da-7bda-4c35-9d77-e991b75c34c4" />

To inspect layer  information:
`docker inspect node:latest`

<img width="343" height="228" alt="image" src="https://github.com/user-attachments/assets/30fdbb67-8af5-4e59-b46f-e0381f8e0237" />

## Where to store images?

In registries that implement OCI distribution-spec. (Docker Hub)
`Registry -> Repository -> Image`
<img width="412" height="262" alt="image" src="https://github.com/user-attachments/assets/1dda2ae2-6dad-4530-bb21-a7f0dd4ea941" />

