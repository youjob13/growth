## What is the image?

Image is a **build-time** construct. You can start multiple containers from a single image.
Image must contains only necessary parts. It can be as slim as possible.
Image does not contain OS kernel. Usualy it contains OS-related filesystem object.
Images (layers) are stored in local repository (cache). Usually located in `var/lib/docker/<storage-driver>`)

<img width="448" height="247" alt="image" src="https://github.com/user-attachments/assets/18b0d05a-037f-4b3f-9eea-e722febf364f" />

## Where to store images?

In registries that implement OCI distribution-spec. (Docker Hub)
Registry -> repository -> Image
