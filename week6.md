Week 6 — Performance Evaluation & Analysis

This week focused on conducting a structured performance evaluation of the Ubuntu virtual machine running inside UTM on macOS. The goal was to benchmark the system under different workloads, analyse CPU, memory, disk, and network behaviour, and identify optimisation opportunities.

1. Testing Methodology

Performance tests were conducted using the following tools:

Metric	Tool
CPU Load	stress-ng, top
Memory Load	stress-ng, free -h
Disk I/O	(VM used shared storage; not stressed heavily this week)
Network Throughput	iperf3 between macOS ↔ Ubuntu VM
Latency	ping, SSH timing
System Stats	top, free -h, ip addr
2. CPU Performance Testing

I installed stress-ng and executed a 4-core CPU stress test for 30 seconds:

stress-ng --cpu 4 --metrics-brief --timeout 30s

📸 CPU Stress Installation

📸 CPU Stress Test Output

📸 CPU Utilisation in top

Observations:

CPU load spiked to near 100% utilisation across all 4 virtual CPU cores.

The system remained responsive but with noticeable UI lag.

bogo ops/s averaged ~1743 ops/s, indicating good VM performance considering it is running on Apple Silicon virtualisation.

3. Memory Performance Testing

Memory stress was tested with:

stress-ng --vm 2 --vm-bytes 1G --metrics-brief --timeout 20s
free -h

📸 Memory Stress Test Output

📸 Memory State After Stress Test

Observations:

VM consumed an additional 1GB of RAM, total usage rising from ~1.3GB to ~2.3GB.

System remained stable with no swapping required.

Memory throughput reached ~307,429 ops/sec.

4. Network Performance Testing

Network tests were executed using iperf3:

macOS acted as the server

VM acted as the client

Commands Used

On macOS:

iperf3 -s


On Ubuntu VM:

iperf3 -c 172.17.74.35

📸 macOS Running iperf3 Server

📸 Ubuntu Client Test Results

Throughput Results:

Direction	Speed
VM → macOS	5.20–5.38 Gbits/sec
macOS → VM	5.32 Gbits/sec

This is very high performance due to UTM’s internal virtual network.

5. Network Latency Testing

Ping testing from macOS to VM:

📸 Ping Test Output

Results:

Average latency: 0.92 ms

Packet loss: 0%

Extremely fast due to local virtual networking.

6. SSH Performance Timing

Measured SSH login overhead:

time ssh anwar35s@192.168.64.13 exit

📸 SSH Timing Screenshot

Results:

Real time: 0.36s

Indicates fast authentication and low network overhead.

7. System Information Snapshot
📸 VM IP Configuration

8. Performance Analysis Summary
Findings

CPU bottleneck: When fully loaded, the VM becomes sluggish—expected for multi-core stress tests.

Memory behaviour: System handled 1GB stress without entering swap—healthy configuration.

Network performance: Speeds >5Gbps indicate excellent VM↔host communication using virtio drivers.

Latency: Sub-1ms latency confirms optimal local virtual network performance.

9. Optimisation Actions Implemented
Improvement	Result
Enabled virtio-net driver	Maximised network throughput
Increased VM memory from 2GB → 4GB	Improved stability under memory load
Disabled unused background services	Reduced idle CPU usage
10. Conclusion

Week 6 provided a thorough evaluation of VM performance under realistic workloads. The system performed well, showing strong CPU and network capabilities and stable memory behaviour. These results serve as the baseline for Week 7’s security audit and overall system evaluation.
