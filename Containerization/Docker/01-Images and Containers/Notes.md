# Notes

## Difference between namespaces and cgroups

### **Namespaces = Isolation**

They isolate **what a process can see and access**. Each container gets its own set of namespaces, so it thinks it has its own system.

### 🔸 Types of Linux Namespaces:

| Namespace | What it isolates | Example |
| --- | --- | --- |
| `pid` | Process IDs | Each container has its own PID 1 |
| `net` | Network interfaces, IP addresses, ports | Containers can have different IPs |
| `mnt` | Filesystems and mount points | Container doesn’t see host's filesystem |
| `uts` | Hostname and domain name | Each container can have its own hostname |
| `ipc` | Interprocess communication (shared memory) | Separate IPC between containers |
| `user` | User and group IDs | Root in container ≠ root on host |

### **cgroups = Resource Control**

They limit, prioritize, and measure **how much resources** a process (or container) can use.

### 🔸 What cgroups can manage:

- **CPU** usage
- **Memory** limits
- **Disk I/O**
- **Network bandwidth**
- **Process count**

=================================================================

- To run the docker containers without sudo commands → add user to docker group
- Docker maintains images and containers by **/var/lib/docker** directory