# 02-Variables

```yaml
# at the same level with tasks 

	vars: 
		dir: /etc/dir1 
		file1: "{{ dir }}/file1" # to concatenate
	
		path: "{{ dir }}" 
		# to call the variable
		# spaces , quotes and curly brackets are required 
		
		
		
		#  we can put all vars in seperated file and call it by using 
		vars_files: 
			- file1
	
```

## Most used ansible facts

| **Fact** | **Description** | **Example Value** |
| --- | --- | --- |
| `ansible_hostname` | Hostname (short) | `ubuntu-vm` |
| `ansible_fqdn` | Fully Qualified Domain Name | `ubuntu-vm.local` |
| `ansible_distribution` | OS Name | `Ubuntu` |
| `ansible_distribution_version` | OS version | `22.04` |
| `ansible_architecture` | CPU architecture | `x86_64` |
| `ansible_processor_cores` | Cores per CPU | `2` |
| `ansible_processor_count` | Number of CPUs | `1` |
| `ansible_processor_vcpus` | Total virtual cores | `4` |
| `ansible_memtotal_mb` | Total memory in MB | `4096` |
| `ansible_memfree_mb` | Free memory in MB | `1024` |
| `ansible_interfaces` | List of all network interfaces | `['lo', 'eth0']` |
| `ansible_default_ipv4.address` | Main IP address | `192.168.56.10` |
| `ansible_default_ipv4.gateway` | Default gateway | `192.168.56.1` |
| `ansible_env.HOME` | Home directory of remote user | `/home/ubuntu` |
| `ansible_user_id` | Logged-in user | `ubuntu` |
| `ansible_mounts` | List of mounted partitions | `[{'mount': '/', 'size_total': ...}]` |
| `ansible_os_family` | OS family (RedHat, Debian) | `Debian` |
| `ansible_selinux.status` | SELinux status (if present) | `disabled` |
| `ansible_uptime_seconds` | System uptime in seconds | `123456` |
| `ansible_pkg_mgr` | Default package manager | `apt` / `yum` |