# Performance Analysis

# Performance Analysis

## Type-1 Hypervisor - Proxmox VE

### Configuration

* Hypervisor: Proxmox VE
* Guest OS: Ubuntu
* vCPU: 2
* RAM: 2048 MB
* Disk: 20 GB
* Network: vmbr0

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


## Type-2 Hypervisor - VMware Workstation

### Configuration

* Hypervisor: VMware Workstation
* Guest OS: Ubuntu
* vCPU: 2
* RAM: 2048 MB
* Disk: 20 GB
* Network: NAT

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
```

## Docker

### Configuration

* Container Platform: Docker
* Host OS: Windows 11
* Container OS: Linux
* Base Image: Python 3.12-slim
* Application: Python Flask Web Application
* Container Port: 5000
* Host Port: 5000
* Container Name: my-python-container
* Docker Image: my-python-app

### Application

A simple Python Flask web application was created and containerized using Docker.

### Files Used

* app.py
* requirements.txt
* Dockerfile

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

### Application Access

```text
http://localhost:5000
```

### Result

The Python Flask web application was successfully containerized using Docker. The Docker image was successfully built, the container was created and started, and the application was accessed through the browser using port 5000. The container was also successfully stopped, restarted, and removed.
