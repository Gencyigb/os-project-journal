Week 3 – Application Selection for Performance Testing

Week 3 focuses on selecting the appropriate applications and tools needed to generate CPU, memory, disk, network and service-level workloads. These tools will later be measured in Week 6 to evaluate system performance and compare baseline vs. stress behaviour.



 1. Workload Application Selection

The applications were chosen to test every major subsystem of the operating system: CPU, memory, disk, network, and service performance.

### Selected Applications for Testing

| Workload Type      | Tool / Application | Purpose & Justification |
|--------------------|-------------------|--------------------------|
| **CPU**            | stress-ng          | Generates controlled CPU stress across multiple cores; ideal for evaluating scheduling and CPU utilisation. |
| **Memory (RAM)**   | memtester          | Allocates and tests large blocks of memory to observe RAM pressure and potential swap usage. |
| **Disk I/O**       | fio                | Industry-standard tool for random/sequential read/write benchmarks and latency measurement. |
| **Network**        | iperf3             | Measures network bandwidth, latency, and reliability between workstation and server. |
| **Web Service**    | nginx              | Lightweight and efficient web server used to test real-world request handling and response time. |


These tools collectively provide complete coverage of system performance metrics.


2. Installation Documentation (via SSH)

All installations were performed remotely from the iMac workstation using SSH.

Commands used:

# Update package lists
sudo apt update

# Install tools for CPU, RAM, disk, network, and service testing
sudo apt install -y stress-ng memtester fio iperf3 nginx

# Verify installation
stress-ng --version
fio --version
iperf3 --version
nginx -v

Screenshot:

	•	[APT install tools](images/week3-install.png)
  
	•	[Version checks](images/week3-versions.png)


 3. Expected Resource Usage Profiles

Before running tests, I documented what behaviour each tool is expected to generate.

### Expected Behaviour per Tool

| Tool        | Expected Resource Usage | Notes |
|-------------|--------------------------|-------|
| **stress-ng** | Very high CPU utilisation (up to 100%) | Used to evaluate CPU saturation and system responsiveness. |
| **memtester** | High RAM usage; may trigger swap if memory is limited | Helps understand memory pressure and OS behaviour. |
| **fio**       | High disk read/write throughput and potential I/O bottlenecks | Useful for identifying disk performance limitations. |
| **iperf3**    | High sustained network throughput | Measures LAN network speed between workstation and server. |
| **nginx**     | Moderate CPU + memory usage depending on request load | Tests application-level behaviour and server response times. |

These expectations help validate whether the system behaves normally or unusually during Week 6 tests.


4. Monitoring Plan Per Workload

This section defines the monitoring commands that will be used later to observe system behaviour during tests.

CPU – stress-ng

	•	Commands: top, htop, vmstat 1 10
  
	•	Metrics: CPU %, load average, process scheduling

Memory – memtester

	•	Commands: free -h, vmstat 1 10
  
	•	Metrics: RAM usage, swap activity

Disk – fio

	•	Commands: iostat -xz 1 10, df -h
  
	•	Metrics: throughput (MB/s), IOPS, latency

Network – iperf3

	•	Commands: iperf3 -s on server, iperf3 -c on workstation
  
	•	Metrics: bandwidth, retransmits, latency (ping)

Web service – nginx

	•	Commands: curl -I http://SERVER_IP, top, access logs
  
	•	Metrics: response times, CPU load per request



5. Why These Tools Were Selected (Academic Justification)
   
	•	They are industry-standard, widely documented, and reliable.

	•	Each tool isolates a specific subsystem — making performance analysis clearer.

	•	The tools generate both baseline and stress workloads.

	•	All tools run entirely in the Linux command line, supporting LO4.

	•	Their output is measurable, allowing for graphs and tables in Week 6.

This ensures a complete and justifiable performance evaluation approach.



 Screenshot:


	•	[stress-ng installed](images/week3-stressng.png)
  
	•	[fio installed](images/week3-fio.png)
  
	•	[iperf3 installed](images/week3-iperf3.png)
  
	•	[nginx installed](images/week3-nginx.png)



6. Week 3 Reflection

Week 3 translated the performance plan into a concrete set of tools and monitoring strategies. Selecting these applications ensured full subsystem coverage and supported clear, quantifiable evaluation in Week 6. This also reinforced the importance of preparing a controlled testing environment so later results can be meaningfully compared and analysed.
