# Performance Analysis of Type-1 and Type-2 Hypervisors

## Type-1 Hypervisor – Proxmox VE

### Configuration

* Hypervisor: Proxmox VE
* Hypervisor Type: Type-1
* Guest OS: Ubuntu
* vCPU: 2
* RAM: 2048 MB
* Disk: 20 GB
* Network: vmbr0
* Benchmark Tool: Sysbench

### Commands Used and Their Purpose

| Command                                  | Purpose                                                           |
| ---------------------------------------- | ----------------------------------------------------------------- |
| `hostnamectl`                            | Displays the system and operating system information.             |
| `lscpu`                                  | Displays CPU architecture and processor information.              |
| `free -h`                                | Displays RAM and memory usage in human-readable format.           |
| `df -h`                                  | Displays disk-space usage of the file systems.                    |
| `top`                                    | Displays running processes and current CPU and memory usage.      |
| `ping -c 3 google.com`                   | Checks network connectivity and measures response time.           |
| `sudo apt update`                        | Updates the Ubuntu package information.                           |
| `sudo apt install sysbench -y`           | Installs the Sysbench benchmarking tool.                          |
| `sysbench --version`                     | Displays the installed Sysbench version.                          |
| `sysbench cpu --cpu-max-prime=20000 run` | Runs a CPU benchmark using prime-number calculations up to 20000. |

---

## Type-2 Hypervisor – VMware Workstation

### Configuration

* Hypervisor: VMware Workstation
* Hypervisor Type: Type-2
* Guest OS: Ubuntu
* vCPU: 2
* RAM: 2048 MB
* Disk: 20 GB
* Network: NAT
* Benchmark Tool: Sysbench

### Commands Used and Their Purpose

| Command                                  | Purpose                                                           |
| ---------------------------------------- | ----------------------------------------------------------------- |
| `hostnamectl`                            | Displays the system and operating system information.             |
| `lscpu`                                  | Displays CPU architecture and processor information.              |
| `free -h`                                | Displays RAM and memory usage in human-readable format.           |
| `df -h`                                  | Displays disk-space usage of the file systems.                    |
| `top`                                    | Displays running processes and current CPU and memory usage.      |
| `ping -c 3 google.com`                   | Checks network connectivity and measures response time.           |
| `sudo apt update`                        | Updates the Ubuntu package information.                           |
| `sudo apt install sysbench -y`           | Installs the Sysbench benchmarking tool.                          |
| `sysbench --version`                     | Displays the installed Sysbench version.                          |
| `sysbench cpu --cpu-max-prime=20000 run` | Runs a CPU benchmark using prime-number calculations up to 20000. |

---

## Docker

### Container-Based Application

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

The application displays:

```text
Hello! My first Docker application is running.
```

### Files Used

* `app.py` – Flask web application
* `requirements.txt` – Flask dependency
* `Dockerfile` – Instructions for building the Docker image

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

| Command                                                               | Purpose                                                                          |
| --------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `wsl --version`                                                       | Displays the installed WSL version.                                              |
| `docker --version`                                                    | Displays the installed Docker version.                                           |
| `docker run hello-world`                                              | Tests whether Docker can successfully run a container.                           |
| `docker buildx build --load -t my-python-app .`                       | Builds the Docker image named `my-python-app`.                                   |
| `docker images`                                                       | Lists the Docker images available on the system.                                 |
| `docker run -d -p 5000:5000 --name my-python-container my-python-app` | Creates and starts the container and maps host port 5000 to container port 5000. |
| `docker ps`                                                           | Displays currently running containers.                                           |
| `docker logs my-python-container`                                     | Displays the logs generated by the container.                                    |
| `docker stop my-python-container`                                     | Stops the running container.                                                     |
| `docker ps`                                                           | Checks the running containers after stopping the container.                      |
| `docker start my-python-container`                                    | Starts the stopped container again.                                              |
| `docker ps`                                                           | Checks whether the container is running again.                                   |
| `docker stop my-python-container`                                     | Stops the container before removal.                                              |
| `docker rm my-python-container`                                       | Removes the Docker container.                                                    |
| `docker ps -a`                                                        | Displays all containers, including stopped containers.                           |
| `docker images`                                                       | Verifies that the Docker image is still available after container removal.       |

### Accessing the Application

The Flask application was accessed through the browser using:

```text
http://localhost:5000
```

### Result

The Docker image was successfully built and the container was created and started successfully. The Flask application was accessed through the mapped host port 5000.

The container was also successfully stopped, restarted, and finally removed while the Docker image remained available.

---

## Comparison of Type-1 and Type-2 Hypervisors

### Configuration Comparison

| **Feature**     | **Type-1: Proxmox VE** | **Type-2: VMware Workstation** |
| --------------- | ---------------------- | ------------------------------ |
| Hypervisor Type | Type-1                 | Type-2                         |
| Guest OS        | Ubuntu                 | Ubuntu                         |
| vCPU            | 2                      | 2                              |
| RAM             | 2048 MB                | 2048 MB                        |
| Disk            | 20 GB                  | 20 GB                          |
| Network         | vmbr0                  | NAT                            |
| Benchmark Tool  | Sysbench               | Sysbench                       |

### Performance Comparison

| **Metric**           | **Type-1: Proxmox VE** | **Type-2: VMware Workstation** |
| -------------------- | ---------------------: | -----------------------------: |
| CPU Benchmark        |           Sysbench CPU |                   Sysbench CPU |
| CPU Prime Limit      |                  20000 |                          20000 |
| Number of Threads    |                      1 |                              1 |
| Total Execution Time |        10.0006 seconds |                10.0005 seconds |
| Total Events         |                  16903 |                         181042 |
| Events per Second    |                1689.43 |                       18101.20 |
| Average Latency      |                0.59 ms |                        0.05 ms |

### Performance Graphs

The following graphs show the measured performance comparison between Proxmox VE and VMware Workstation:

* CPU Events per Second
* Total Execution Time
* Average Latency
* Allocated Memory
