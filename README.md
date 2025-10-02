# DevOps Internship – Task 7 (Netdata Monitoring via Docker)

## 📌 Objective
Install and run **Netdata** using Docker to monitor system and application performance metrics.

## ⚠️ Environment Issue
**Note:** The Docker environment provided for this task was non-functional. All `docker` commands timed out, preventing the live execution of the Netdata container. The log files in the `logs/` directory are simulated as a result.

## 🛠 Tools Used
- Netdata
- Docker

## 🚀 Steps to Run

### 1. Run Netdata Container
```bash
docker run -d \
  --name=netdata \
  -p 19999:19999 \
  --cap-add SYS_PTRACE \
  --security-opt apparmor=unconfined \
  -v netdataconfig:/etc/netdata \
  -v netdatalib:/var/lib/netdata \
  -v netdatacache:/var/cache/netdata \
  netdata/netdata
```
Note: Port mapping is -p 19999:19999 (default Netdata UI port)

### 2. Access the Dashboard
Open your browser and go to:
```arduino
http://localhost:19999
```
### 3. Explore Features
Charts: CPU, RAM, Disk I/O, Network, Docker containers, etc.

Alerts: See active & historical alerts for your system.

Custom Metrics: Add plugins or collect app-specific metrics.

### 4. Export Logs
To export logs:
```bash
docker exec netdata cat /var/log/netdata/error.log > logs/netdata-error.log
docker exec netdata cat /var/log/netdata/access.log > logs/netdata-access.log
```
Or mount a volume:
```bash
-v ./logs:/var/log/netdata
```
### 5. Stop & Remove Container
```bash
docker stop netdata
docker rm netdata
```
📂 Repo Structure
```pgsql
netdata-task7/
│
├── README.md
├── logs/
│   ├── netdata-error.log (to be filled after running)
│   └── netdata-access.log (to be filled after running)
```
📤 Submission
After running Netdata locally:

Export logs into the logs/ folder

Push the repo to GitHub

Submit the link here:
Google Form Link

📚 Key Learning
How to quickly deploy a monitoring solution with Docker

Understanding CPU, memory, disk, and network metrics

Visualizing and reacting to performance alerts
