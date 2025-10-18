# Explain

# Types of Partitions in Ubuntu

## Primary Partitions

Primary partitions are the main partitions on a disk. Traditional MBR partitioning allows for a maximum of 4 primary partitions per disk. These partitions can be used directly to store data or install operating systems.

```bash
# View primary partitions
sudo fdisk -l | grep "^/dev"

```

## Extended Partition

An extended partition is a special type of primary partition that acts as a container for logical partitions. It's a solution to the MBR limitation of 4 primary partitions. You can only have one extended partition per disk.

Extended partitions don't hold data directly but serve as containers for logical partitions.

## Logical Partitions

Logical partitions exist within the extended partition. You can create many logical partitions within a single extended partition, effectively bypassing the 4-partition limit of MBR.

In Ubuntu, logical partitions are typically labeled as /dev/sdaX where X is 5 or higher (partitions 1-4 are reserved for primary partitions).

## GPT Partitions

GUID Partition Table (GPT) is a newer standard that replaces the limitations of MBR. GPT supports up to 128 partitions by default and disks larger than 2TB. Modern Ubuntu installations often use GPT, especially on UEFI systems.

```bash
# Check if your disk uses GPT
sudo parted -l | grep "Partition Table"

```

## Functional Partition Types in Ubuntu

| **Partition Type** | **Mount Point** | **Purpose** | **Recommended Size** | **Notes** |
| --- | --- | --- | --- | --- |
| **Root** | `/` | Core system files, binaries, libraries, etc. | 20–50 GB+ | Required for every Linux install |
| **Boot** | `/boot` | Stores kernel and bootloader files | 512 MB – 1 GB | Needed if using separate `/boot`, especially with LVM or encryption |
| **EFI System** | `/boot/efi` | Used for booting in UEFI systems | 100–500 MB | Required for UEFI; formatted as FAT32 |
| **Home** | `/home` | User files, configs, desktop, downloads, etc. | Varies (rest of disk) | Optional but highly recommended for user data separation |
| **Swap** | (No mount) | Used as virtual memory when RAM is full | 1–2x RAM (up to 8 GB max) | Optional; needed for hibernation |
| **Var** | `/var` | Variable data: logs, spool, packages | 1–5 GB+ | Useful for servers (log-heavy systems) |
| **Tmp** | `/tmp` | Temporary files | 512 MB – 2 GB | Cleared on reboot unless configured otherwise |
| **Usr** | `/usr` | Read-only user binaries and applications | 5–20 GB+ | Often large; part of `/` unless separated |
| **Opt** | `/opt` | Optional/3rd-party software | Optional | Used in enterprise apps |
| **Srv** | `/srv` | Data for services (e.g. web servers) | Optional | Useful on servers |
| **Recovery** | (No mount) | Partition for system recovery tools | Optional | May exist in OEM installations |

### /etc/fstab

- Automatically mounts disks, partitions, or network drives at boot.
- Ensures the system knows where each storage device should appear in the file system (like `/`, `/home`, `/mnt/data`, etc.).
- Checks partitions and we can make permanently changes to make it check or not as we want

---

# File system

- A **file system** is a method used by an operating system to **store, organize, and access data** on a storage device like a hard disk, SSD, or USB.

### Types :

| **File System** | **Usage** | **Features** | **Max File Size** | **Max Volume Size** |
| --- | --- | --- | --- | --- |
| **ext4** | Most common in Ubuntu and modern distros | Journaling, robust, fast | 16 TB | 1 EB (exabyte) |
| **ext3** | Older journaling system | Extends ext2 with journaling | 2 TB | 32 TB |
| **ext2** | Legacy (no journaling) | Lightweight, useful for flash drives | 2 TB | 32 TB |
| **XFS** | High-performance file system | Best for large files, parallel I/O | 8 EB | 8 EB |
| **Btrfs** | Advanced features (snapshots, compression) | Copy-on-write, self-healing | 16 EB | 16 EB |
| **vfat / FAT32** | USB drives, compatibility | Cross-platform, limited features | 4 GB | 2 TB |
| **NTFS** | Windows file system | Read/write support on Linux | 16 TB | 256 TB |

### What file system creates :

| **Item** | **Location** | **Purpose** |
| --- | --- | --- |
| **Superblock** | Hidden inside file system | Metadata about the file system itself (size, mount count, UUID, etc.) |
| **Inodes** | Stored in inode table | Each file has an inode that stores permissions, size, timestamps, etc. (not the name!) |
| **lost+found** | `/lost+found` in each ext* file system | Used by `fsck` to store orphaned/recovered files |
| **Mount Point** | Example: `/`, `/home`, `/boot` | Location where the file system is attached in the Linux directory |

### Inode table :

- Each partition has inode table which has all info about it and its files (type - permissions - GID - num of links - file owner ID )
- It has limited and fixed number of indices that if it was full → no more files can be created even you have available storage (it depends on file system type)

# Logical Volumes

- Used to make volume groups then we can modify the partitions by shrinking or adding more disks → gives us a lot of flexibility to deal with storage