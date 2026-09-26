<h1>Performance Analysis</h1>

<h2>Type-1 Hypervisor - Proxmox VE</h2>

<h3>Configuration</h3>

<ul>
<li>Hypervisor: Proxmox VE</li>
<li>Hypervisor Type: Type-1</li>
<li>Guest OS: Ubuntu</li>
<li>vCPU: 2</li>
<li>RAM: 2048 MB</li>
<li>Disk: 20 GB</li>
<li>Network: vmbr0</li>
<li>Benchmark Tool: Sysbench</li>
</ul>

<h3>Commands Used</h3>

<pre>
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
</pre>

<h2>Type-2 Hypervisor - VMware Workstation</h2>

<h3>Configuration</h3>

<ul>
<li>Hypervisor: VMware Workstation</li>
<li>Hypervisor Type: Type-2</li>
<li>Guest OS: Ubuntu</li>
<li>vCPU: 2</li>
<li>RAM: 2048 MB</li>
<li>Disk: 20 GB</li>
<li>Network: NAT</li>
<li>Benchmark Tool: Sysbench</li>
</ul>

<h3>Commands Used</h3>

<pre>
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
</pre>

<h2>Docker</h2>

<h3>Container-Based Application</h3>

<h3>Configuration</h3>

<ul>
<li>Container Platform: Docker</li>
<li>Host OS: Windows 11</li>
<li>Container OS: Linux</li>
<li>Base Image: Python 3.12-slim</li>
<li>Application: Python Flask Web Application</li>
<li>Container Port: 5000</li>
<li>Host Port: 5000</li>
<li>Container Name: my-python-container</li>
<li>Docker Image: my-python-app</li>
</ul>

<h3>Application</h3>

<p>A simple Python Flask web application was created and containerized using Docker.</p>

<p>The application displays:</p>

<pre>
Hello! My first Docker application is running.
</pre>

<h3>Files Used</h3>

<ul>
<li>app.py – Flask web application</li>
<li>requirements.txt – Flask dependency</li>
<li>Dockerfile – Instructions for building the Docker image</li>
</ul>

<h3>Dockerfile</h3>

<pre>
FROM python:3.12-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY app.py .
EXPOSE 5000
CMD ["python", "app.py"]
</pre>

<h3>Commands Used</h3>

<pre>
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
</pre>

<h3>Accessing the Application</h3>

<p>The Flask application was accessed through the browser using:</p>

<pre>http://localhost:5000</pre>

<h3>Result</h3>

<p>The Docker image was successfully built and the container was created and started successfully. The Flask application was accessed through the mapped host port 5000.</p>

<p>The container was also successfully stopped, restarted, and finally removed while the Docker image remained available.</p>

<h2>Comparison of Type-1 and Type-2 Hypervisors</h2>

<h3>Configuration Comparison</h3>

<table>
<tr>
<th>Feature</th>
<th>Type-1: Proxmox VE</th>
<th>Type-2: VMware Workstation</th>
</tr>
<tr>
<td>Hypervisor Type</td>
<td>Type-1</td>
<td>Type-2</td>
</tr>
<tr>
<td>Guest OS</td>
<td>Ubuntu</td>
<td>Ubuntu</td>
</tr>
<tr>
<td>vCPU</td>
<td>2</td>
<td>2</td>
</tr>
<tr>
<td>RAM</td>
<td>2048 MB</td>
<td>2048 MB</td>
</tr>
<tr>
<td>Disk</td>
<td>20 GB</td>
<td>20 GB</td>
</tr>
<tr>
<td>Network</td>
<td>vmbr0</td>
<td>NAT</td>
</tr>
<tr>
<td>Benchmark Tool</td>
<td>Sysbench</td>
<td>Sysbench</td>
</tr>
</table>

<h3>Performance Comparison</h3>

<table>
<tr>
<th>Metric</th>
<th>Type-1: Proxmox VE</th>
<th>Type-2: VMware Workstation</th>
</tr>
<tr>
<td>CPU Benchmark</td>
<td>Sysbench CPU</td>
<td>Sysbench CPU</td>
</tr>
<tr>
<td>CPU Prime Limit</td>
<td>20000</td>
<td>20000</td>
</tr>
<tr>
<td>Number of Threads</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>Total Execution Time</td>
<td>10.0006 seconds</td>
<td>10.0005 seconds</td>
</tr>
<tr>
<td>Total Events</td>
<td>16903</td>
<td>181042</td>
</tr>
<tr>
<td>Events per Second</td>
<td>1689.43</td>
<td>18101.20</td>
</tr>
<tr>
<td>Average Latency</td>
<td>0.59 ms</td>
<td>0.05 ms</td>
</tr>
</table>

<h3>Performance Graphs</h3>

<p>The following graphs show the measured performance comparison between Proxmox VE and VMware Workstation:</p>

<ul>
<li>CPU Events per Second</li>
<li>Total Execution Time</li>
<li>Average Latency</li>
<li>Allocated Memory</li>
</ul>
