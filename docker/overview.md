## Why do we need Docker?

### First Chapter - Problem

Business needs the application. In old days **for each application dedicated server is required**. So business had to buy server **in advance**. 
The problem is that we actually cann't guess the performance of our future apps. So business could buy very expensive, fast and performant server that out application wouldn't utilize even on 50%!
Or vise versa, business could buy a cheap server that couldn't run our application. 

### Second Chapter - Virtual Machine (VM) game changer

**Pros:** VM allows us to run multiple business applications on a single server safely.
**Cons:** 
1) Every VM needs its own dedicated OS. Every OS consumes CPU, RAM and other resources that our business applications should use!;
2) Every VM and OS needs patching;
3) Every VM and OS needs monitoring;
4) VMs are slow to boot.

### Third Chapter - Containers

**Pros:** container shares the OS of the host it's running on => **single host can run more containers than VMs**. Containers far more efficient than VMs. Containers are also faster and more porable than VMs.

### Fourth Chapter - Linux VS Windows containers.

It's vital to understand that **containers share the kernel of the host they're running on**. 
Containerized Windows apps need a host with Windows kernel. (You can run Linux containers on Windows system that have the WSL 2)
Containerized Linux apps need a host with Linux kernel. (Most of the modern containers are linux containers)

### Docker

Docker platform is a packaged collection of technologies for creating, managing and orchestrating containers.
Docker platform consist of the two major parts:
```cmd
The CLI (client); --API calss--> The engine (server).
```

