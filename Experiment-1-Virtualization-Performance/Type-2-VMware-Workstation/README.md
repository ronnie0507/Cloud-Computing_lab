# Type-2 Hypervisor – VMware Workstation

## Overview

VMware Workstation is a Type-2 hypervisor that runs on top of a host operating system. In this experiment, an Ubuntu virtual machine was created using VMware Workstation, and its CPU performance was evaluated using Sysbench.

This setup represents a hosted virtualization environment, where the hypervisor runs inside an existing operating system rather than directly on the hardware.

## 1. Virtual Machine Specifications

| Parameter       | Configuration                 |
| --------------- | ----------------------------- |
| Hypervisor      | VMware Workstation            |
| Hypervisor Type | Type-2                        |
| VM Name         | CC-Experiment1-Type2          |
| Guest OS        | Ubuntu 64-bit                 |
| CPU             | 2 vCPU (1 processor, 2 cores) |
| Memory          | 8 GB (8192 MB)                |
| Disk            | 20 GB                         |
| Network         | NAT                           |

## 2. System Verification

The following commands were used to verify the Ubuntu VM and confirm that the system was running normally.

```bash
hostnamectl
lscpu
free -h
df -h
top
```

## 3. CPU Performance Benchmark

Sysbench was installed and used to measure the processing capability of the virtual machine.

### Installation

```bash
sudo apt update
sudo apt install sysbench -y
sysbench --version
```

### Execution

```bash
sysbench cpu --cpu-max-prime=20000 run
```

## 4. Observations and Results

The benchmark produced the following result for the VMware Workstation environment.

| Metric               |    Result |
| -------------------- | --------: |
| Total Execution Time | 10.0003 s |
| Total Events         |     17588 |
| Events per Second    |   1758.60 |
| Minimum Latency      |   0.55 ms |
| Average Latency      |   0.57 ms |
| Maximum Latency      |   1.11 ms |

## 5. Workflow

1. Launch VMware Workstation.
2. Create a new virtual machine and select the Ubuntu ISO.
3. Configure the VM with 2 vCPUs and 8 GB of RAM.
4. Allocate a 20 GB virtual disk and choose NAT networking.
5. Install Ubuntu and complete the VM setup.
6. Verify the system resources using the Linux commands listed above.
7. Install Sysbench and run the CPU benchmark.
8. Record the performance results and power off the VM after testing.

## Conclusion

This configuration demonstrates how a Type-2 hypervisor can be used to create and test a Ubuntu VM in a hosted virtualization environment. The CPU benchmark was successfully executed, and the system was validated for resource usage and performance metrics.
