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




