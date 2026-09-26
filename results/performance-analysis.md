# Performance Analysis

## Type-1 Hypervisor - Proxmox VE

### Configuration

* Hypervisor: Proxmox VE
* Hypervisor Type: Type-1
* Guest OS: Ubuntu
* vCPU: 2
* RAM: 2048 MB
* Disk: 20 GB
* Network: vmbr0
* Benchmark Tool: Sysbench

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
## Type-2 Hypervisor - VMware Workstation

### Configuration

* Hypervisor: VMware Workstation
* Hypervisor Type: Type-2
* Guest OS: Ubuntu
* vCPU: 2
* RAM: 2048 MB
* Disk: 20 GB
* Network: NAT
* Benchmark Tool: Sysbench

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

## Container-Based Application

### Configuration

- Container Platform: Docker
- Host OS: Windows 11
- Container OS: Linux
- Base Image: Python 3.12-slim
- Application: Python Flask Web Application
- Container Port: 5000
- Host Port: 5000
- Container Name: `my-python-container`
- Docker Image: `my-python-app`

### Application

A simple Python Flask web application was created and containerized using Docker.

The application displays:

```text
Hello! My first Docker application is running.
```

### Files Used

- `app.py` – Flask web application
- `requirements.txt` – Flask dependency
- `Dockerfile` – Instructions for building the Docker image

### Dockerfile

```dockerfile
FROM python:3.12-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY app.py .
EXPOSE 5000
CMD ["python", "app.py"]
```

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
docker ps
docker start my-python-container
docker ps
docker stop my-python-container
docker rm my-python-container
docker ps -a
docker images
```

### Accessing the Application

The Flask application was accessed through the browser using:

```text
http://localhost:5000
```

### Result

The Docker image was successfully built and the container was created and started successfully. The Flask application was accessed through the mapped host port `5000`.

The container was also successfully stopped, restarted, and finally removed while the Docker image remained available.
## Comparison of Type-1 and Type-2 Hypervisors

### Configuration Comparison

| Feature | Type-1: Proxmox VE | Type-2: VMware Workstation |
|---|---|---|
| Hypervisor Type | Type-1 | Type-2 |
| Guest OS | Ubuntu | Ubuntu |
| vCPU | 2 | 2 |
| RAM | 2048 MB | 2048 MB |
| Disk | 20 GB | 20 GB |
| Network | vmbr0 | NAT |
| Benchmark Tool | Sysbench | Sysbench |

### Performance Comparison

| Metric | Type-1: Proxmox VE | Type-2: VMware Workstation |
|---|---:|---:|
| CPU Benchmark | Sysbench CPU | Sysbench CPU |
| CPU Prime Limit | 20000 | 20000 |
| Number of Threads | 1 | 1 |
| Total Execution Time | 10.0006 seconds | 10.0005 seconds |
| Total Events | 16903 | 181042 |
| Events per Second | 1689.43 | 18101.20 |
| Average Latency | 0.59 ms | 0.05 ms |

### Performance Graphs

The following graphs show the measured performance comparison between Proxmox VE and VMware Workstation:

- CPU Events per Second
- Total Execution Time
- Average Latency
- Allocated Memory