# ⚙️ Week 3 – Application Selection for Performance Testing

Week 3 focused on selecting the tools required to generate CPU, memory, disk, network, and service-level workloads. These applications form the basis of the performance tests conducted in Week 6. The goal was to choose tools that provide reliable, measurable, and repeatable results while operating entirely through the command line.

---

## Workload Application Selection

A set of specialised tools was chosen to evaluate the behaviour of the system under different types of stress. Each application targets a specific subsystem and provides quantitative output suitable for analysis.

```markdown
| Workload Type      | Tool / Application | Purpose |
|--------------------|-------------------|---------|
| **CPU**            | stress-ng          | Generates controlled CPU load for analysing scheduler behaviour and utilisation levels. |
| **Memory**         | memtester          | Allocates and tests large blocks of RAM to observe memory pressure and swap activity. |
| **Disk I/O**       | fio                | Performs sequential and random read/write operations with configurable block sizes. |
| **Network**        | iperf3             | Measures bandwidth and connection stability between workstation and server. |
| **Web Service**    | nginx              | Serves lightweight HTTP responses for evaluating service responsiveness. |
```



---

## Installation of Workload Tools

The selected applications were installed on the server to support the performance methodology defined in Week 2.

```bash
sudo apt update
sudo apt install -y stress-ng memtester fio iperf3 nginx
```

Version checks confirmed successful installation:

```bash
stress-ng --version
fio --version
iperf3 --version
nginx -v
```



---

## Expected Resource Usage Profiles

Each tool was reviewed to understand its expected impact on the system. This helped prepare the monitoring plan and ensured that the system’s behaviour under load was predictable and measurable.

```markdown
| Tool        | Expected Resource Behaviour |
|-------------|-----------------------------|
| **stress-ng** | High CPU utilisation, increased load averages. |
| **memtester** | Significant RAM usage, possible swap use on smaller systems. |
| **fio**       | High disk throughput, increased latency under heavy I/O. |
| **iperf3**    | High network bandwidth usage between endpoints. |
| **nginx**     | Light CPU and memory usage with quick response times. |
```



---

## Monitoring Plan

The monitoring approach for Week 6 was designed to capture real-time system behaviour during each workload test. These commands were selected for their ability to measure CPU activity, memory usage, disk I/O, and network behaviour effectively.

```bash
top -bn1 | head -n 5
vmstat 1 5
iostat -xz 1 5
df -h
free -h
ss -s
ping -c 5 SERVER_IP
```


---

## Reflection

Week 3 established the technical tools required to conduct meaningful performance testing. By selecting command-line driven applications with predictable behaviour, the system was prepared for detailed workload evaluation. Each tool supports analysis of a specific subsystem, enabling a structured approach to system measurement in Week 6. This preparation strengthened command-line proficiency and ensured a consistent methodology for later performance analysis.
