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

---

## Comparison

| Parameter | Type-1: Proxmox VE | Type-2: VMware Workstation | Docker |
|---|---|---|---|
| Technology | Proxmox VE | VMware Workstation | Docker |
| Type | Type-1 Hypervisor | Type-2 Hypervisor | Container Platform |
| Host OS | Proxmox host | Windows 11 | Windows 11 |
| Guest/Container OS | Ubuntu | Ubuntu | Linux |
| vCPU | 2 | 2 | Uses host CPU |
| RAM | 2048 MB | 2048 MB | Uses host resources |
| Disk | 20 GB | 20 GB | Uses container/image storage |
| Network | vmbr0 | NAT | Port 5000 |
| Application | Ubuntu VM | Ubuntu VM | Python Flask |
| Benchmark | Sysbench CPU | Sysbench CPU | Flask application |
| Main Purpose | Virtual machine management | Virtual machine management | Application containerization |

### Performance Comparison

| Metric | Type-1: Proxmox VE | Type-2: VMware Workstation |
|---|---:|---:|
| Total Execution Time | 10.0006 seconds | Recorded in Type-2 screenshot |
| Total Events | 16,903 | Recorded in Type-2 screenshot |
| Events per Second | 1,689.43 | Recorded in Type-2 screenshot |
| Average Latency | 0.59 ms | Recorded in Type-2 screenshot |

### Comparison Result

The Type-1 and Type-2 hypervisors were tested using Ubuntu virtual machines with 2 vCPUs, 2048 MB RAM and a 20 GB virtual disk. The same Sysbench CPU benchmark with a prime number limit of 20,000 was used for both hypervisors.

Proxmox VE was tested as a Type-1 hypervisor and produced a Sysbench result of 1,689.43 events per second with an average latency of 0.59 ms.

VMware Workstation was tested as a Type-2 hypervisor using the same benchmark. Its measured values are available in the Type-2 Sysbench screenshot.

Docker was evaluated separately as a container platform. Unlike the two hypervisors, Docker runs applications inside containers instead of running a complete guest operating system in a virtual machine.

Therefore, Proxmox VE and VMware Workstation are compared as virtualization technologies, while Docker is considered a containerization technology.
