- If you are currently using docker, but bebind a firewall,... and docker need to run over proxy, then this is tutorial for building image
## HTTP Proxy
- If you're using http-proxy, then just build as normal (proxy is on host, not in docker environment in my case)
```bash
DOCKER_BUILDKIT=0 docker build --network=host \
             --build-arg HTTP_PROXY=http://127.0.0.1:8080 \
             --build-arg HTTPS_PROXY=http://127.0.0.1:8080 \
             -t vol2 .
```
- After building process done, there will exist **vol2** image, run **docker image ls** to check
## SOCKS Proxy
- In default, docker does not support socks connection without upgrading license. Suppose that you are using socks5 proxy at **socks5://127.0.0.1:1080**, you need a intermediary http proxy to forward traffic to socks5 proxy, I will use **privoxy**
- Install privoxy
```bash
sudo apt-get update 
sudo apt-get install privoxy
```
- Modify config file
```bash
sudo nano /etc/privoxy/config

listen-address 0.0.0.0:8118
forward-socks5t / 127.0.0.1:1080 .
```
- Restart service
```bash
sudo systemctl restart privoxy
```
- Run docker build through privoxy proxy (Use Host Networking in Docker)
```bash
DOCKER_BUILDKIT=0 docker build --network=host \
             --build-arg HTTP_PROXY=http://127.0.0.1:8118 \
             --build-arg HTTPS_PROXY=http://127.0.0.1:8118 \
             -t vol2 .
```
- After building process done, there will exist **vol2** image, run **docker image ls** to check