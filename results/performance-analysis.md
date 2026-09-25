# Performance Analysis

## Type-2 Hypervisor - VMware Workstation

### Configuration

- Hypervisor: VMware Workstation
- Guest OS: Ubuntu
- vCPU: 2
- RAM: 2048 MB
- Disk: 20 GB
- Network: NAT

### Commands Used

```bash
hostnamectl
lscpu
free -h
df -h
top
ping -c 3 google.com
sudo apt update
sudo apt install sysbench -y
sysbench --version
sysbench cpu --cpu-max-prime=20000 run



## Container-Based Application - Docker

### Configuration

* Container Platform: Docker
* Host OS: Windows 11
* Container OS: Linux
* Base Image: Python 3.12-slim
* Application: Python Flask Web Application
* Container Port: 5000
* Host Port: 5000

### Commands Used

```bash
wsl --version
docker --version
docker run hello-world
docker buildx build --load -t my-python-app .
docker images
docker run -d -p 5000:5000 --name my-python-container my-python-app
docker ps
docker logs my-python-container
docker stop my-python-container
docker start my-python-container
docker stop my-python-container
docker rm my-python-container
docker ps -a
docker images
```
