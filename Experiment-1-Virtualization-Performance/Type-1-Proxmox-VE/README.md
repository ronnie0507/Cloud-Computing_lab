# Type-1 Hypervisor – Proxmox VE

## Overview

Proxmox VE is a powerful open-source, bare-metal Type-1 hypervisor that runs directly on physical server hardware. In this experiment, an Ubuntu virtual machine was created and deployed through the Proxmox VE web interface. The environment was then checked for system health, and the CPU performance was measured using Sysbench.

This setup demonstrates how a Type-1 hypervisor offers strong virtualization capabilities while allowing efficient resource management and performance testing in a real lab environment.

## 1. Virtual Machine Specifications

| Parameter       | Configuration               |
| --------------- | --------------------------- |
| Hypervisor      | Proxmox VE                  |
| Hypervisor Type | Type-1                      |
| Node            | Selected Proxmox node (pve) |
| VM Name         | CC-Experiment1-Type1        |
| Guest OS        | Linux (Ubuntu 64-bit)       |
| ISO Image       | ubuntu-22.04.iso            |
| CPU             | 2 vCPU (1 socket, 2 cores)  |
| Memory          | 2048 MiB (2 GB)             |
| Disk            | 20 GB (local-lvm)           |
| Network         | vmbr0 (VirtIO)              |

## 2. System Verification

The following commands were used to confirm that the host and guest systems were properly configured and running as expected.

| Verification      | Command       |
| ----------------- | ------------- |
| Hostname & OS     | `hostnamectl` |
| CPU               | `lscpu`       |
| Memory            | `free -h`     |
| Disk              | `df -h`       |
| System Monitoring | `top`         |

## 3. CPU Performance Benchmark

Sysbench was used to evaluate the processing performance of the virtual machine under a CPU-intensive workload.

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

The benchmark produced the following output after the CPU workload was executed successfully.

| Parameter            | Observation |
| -------------------- | ----------: |
| Hypervisor           |  Proxmox VE |
| Hypervisor Type      |      Type-1 |
| Guest OS             |      Ubuntu |
| CPU                  |      2 vCPU |
| Memory               |        2 GB |
| Disk                 |       20 GB |
| Total Execution Time |   10.0006 s |
| Total Events         |       16903 |
| Events per Second    |     1689.43 |
| Minimum Latency      |     0.57 ms |
| Average Latency      |     0.59 ms |
| Maximum Latency      |     1.09 ms |

## 5. Workflow

1. Open the Proxmox VE web interface.
2. Select the Proxmox node and create a new virtual machine.
3. Configure the Ubuntu ISO, CPU, memory, disk, and networking settings.
4. Start the VM and complete the Ubuntu installation.
5. Verify the system using the Linux commands listed above.
6. Install Sysbench and run the CPU benchmark.
7. Record the benchmark results for analysis.
8. Monitor the virtual machine during execution and power it off after testing is complete.

## Conclusion

This experiment highlights the practical use of Proxmox VE as a Type-1 hypervisor for creating and managing virtual machines efficiently. The system was successfully deployed, verified, and benchmarked, showing that Proxmox provides a reliable platform for virtualization testing and performance evaluation.
