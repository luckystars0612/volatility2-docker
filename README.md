# Volatility 2 Docker Build Guide

[![Docker](https://img.shields.io/badge/Docker-Build-blue)](https://www.docker.com/)

This repository provides a **Dockerfile** for building Volatility 2 in a clean and reproducible environment, supporting both **proxy** and **non-proxy** builds.

## 🚀 Quick Start

### 🏗️ Build Without Proxy
- More detail on [docker-nonproxy](./docker-nonproxy/)

### 🌐 Build With Proxy
- More detail on [docker-proxy](./docker-proxy/)

## 🛠️ Usage

- Once built, run Volatility 2 in a container:

```sh
docker run --rm -it vol2 /bin/bash
```

- Or directly analyze a memory dump:

```sh
docker run --rm -it vol2 -f <memory_dump> imageinfo
```

- To access memory dumps from your **host machine**, mount the directory and access interactive bash:

```sh
docker run --rm -it -v /path/to/dumps:/workspace vol2 /bin/bash
```

## 📝 Notes
- Ensure `docker` is installed and running.
- Adjust `http_proxy` and `https_proxy` if using a proxy.
- This image is based on **Debian Buster** with all necessary dependencies preinstalled.

## 🔗 References
- **Official Volatility 2 Repo**: [https://github.com/volatilityfoundation/volatility](https://github.com/volatilityfoundation/volatility)
- **Docker Docs**: [https://docs.docker.com/](https://docs.docker.com/)

## 🔥 Contributions & Issues
Open **issues** or **pull requests** for feedback and improvements.

🔹 **Author**: [luckystars0612](https://github.com/luckystars0612)  

## Support me (optional)
If you find it useful, you can support me with a cup of coffee.

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/Y8Y2123O0D)
