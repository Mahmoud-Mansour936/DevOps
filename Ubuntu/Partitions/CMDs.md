# CMDs

# Partition Management Commands

## To check existing partition layout:

```bash
# Display all disk partitions
sudo lsblk

# Show mounted partitions with usage information
df -h

```

## To create or modify partitions:

```bash
# Interactive partition tool
sudo fdisk /dev/sdX

# More powerful partition tool
sudo parted /dev/sdX
```

# Attaching new volume

## Step 1 : `Partitioning the Disk`

```bash
sudo fdisk /dev/xvdh  # the argument is the path of partition file in dev dir 

Follow the prompts:
1. Press `n` → New Partition
2. Choose `p` for Primary
3. Accept defaults or type `+Size`
4. Press `w` to write changes

# Linux allows **4 primary partitions**. For more, use an **extended partition**,
# and inside it create **logical drives**
```

## Step 2 : `Create File System`

```bash
sudo mkfs.ext4 /dev/xvdh1 : # after (.) we put the filesys. and the argument 
# is the path of partition file in dev dir 

### Common File Systems

| Type   | Description                     | Use Case                      |
|--------|---------------------------------|-------------------------------|
| ext4   | Most common Linux FS            | General purpose (recommended) |
| xfs    | High performance                | Logs or large storage         |
| btrfs  | Snapshot & compression support  | Advanced use                  |
| ntfs   | Windows file system             | Cross-platform sharing        |

```

## Step 3 : `Check File System Health`

```bash
# To scan the partition
sudo fsck /dev/xvdh1

# Auto-fix errors:
sudo fsck -a /dev/xvdh1 

```

## Step 4 : `Mount the File System`

It gives the dir that partition will apply on them , anything on these dirs will be saved on this partition

```bash
# Mount the formatted partition to a directory:

udo mount /dev/xvdh1 /mydir # 1st argument is the path of partition 
# 2nd one is the path of dir u want to mount on it 
# U can mount more than one dir 

# To unmount:

sudo umount /mydir

```

## Info of file system

```bash
df --> displays amount of space of the file system
-h -> easy size reading

du -> Summarizes disk usage of files and directories
-s -> get the sum usage not every file individualy

tube2fs -l /dev/xvdz1 | grep indode --> get indode indicies of file system 
```

# volume group and Logical volume :

## create logical volumes :

### Step 1 : convert physical disk → physical volume

```bash
sudo pvcreate /dev/sdba /dev/sdpd 
# the arguments are the path of hard disks we need to convert to physical volumes 
```

### Step 2 : create volume group

```bash
sudo vgcreate vg0 /dev/sdba /dev/sdpd
# 1st argument is the name of volume group
# last arguments are the path of volumes we need to add to this volume group 
```

### Step 3 : create logical volume

```bash
sudo lvcreate --name lv0 --size 1.5G vg0 
# --name --> to name the logical volume 
# -- size --> to define the size of logical volume we need from volume group 
# last argument is the name of volume group 
```

### Step 4 : create file system mount the logical volume

```bash
sudo mkfs.ext4 /dev/vg0/lv0
sudo fsck /dev/vg0/lv0
sudo mount /dev/vg0/lv0 /mydir

# like the steps of mounting the primary partitions 
```

## Extend logical volumes :

### Step 1 : convert new disk to physical volume

```bash
sudo pvcreate /dev/sdbe 
```

### Step 2 : extend volume group

```bash
sudo vgextend vg0 /dev/sdbe 
# 1st argument the name of volume group we need to extend 
# last arguments are the path of volumes we need to add to this volume group 
```

### Step 3 : extend logical volume

```bash
sudo lvextend -L +200M /dev/vg0/lv0
# -L --> to give the size we need to extend 
# 2nd argument is the path of volume 
```

### Step 4 : resize the file system

```bash
sudo resize2fs /dev/vg0/lv0 # the argument is the path of LV
```

## Remove LVM :

```bash
sudo umount /mydir # path of mounting dir 
sudo lvremove /dev/vg0/lv0 # path of LV
sudo vgremove vg0 # name of VG
sudo pvremove /dev/sdba /dev/sdpd # path of physical Volumes 
```