# Setup Flexible Disk Storage with Logical Volume Management(LVM) in Linux


## Setup Flexible Disk Storage with Logical Volume Management

Check current Physical Volume/Volume Group/Logical Volume information:
	# pvs
	# vgs
	# lvs

Check current available disks:
	# fdisk -l

Check current disk mount information:
	# df -hT

Partition the disk using fdisk:
	# fdisk -cu /dev/sdx
	# fdisk -cu /dev/sdy
	# fdisk -cu /dev/sdz

Create physical volumes:
	# pvcreate /dev/sdx1 /dev/sdy1 /dev/sdz1

Create volume groups(with PE size 32M):
	# vgcreate -s 32M new_add_vg /dev/sdx1 /dev/sdy1 /dev/sdz1

Create logical volumes:
* Method 1: Creating Logical Volumes using PE Size's
	# vgdisplay new_add_vg
	# lvcreate -l 575 -n lv_document new_add_vg
	# lvcreate -l 575 -n lv_public new_add_vg
	# lvcreate -l 575 -n lv_manager new_add_vg

* Method 2: Creating Logical Volumes using GB Size's
	# lvcreate -L 18G -n lv_document new_add_vg
	# lvcreate -L 18G -n lv_public new_add_vg
	# lvcreate -L 18G -n lv_manager new_add_vg

Create file system:
	# mkfs.ext4 /dev/new_add_vg/lv_document
	# mkfs.ext4 /dev/new_add_vg/lv_manager
	# mkfs.ext4 /dev/new_add_vg/lv_public

Mount the logical volumes to /mnt:
	# mkdir /mnt/{lv_document,manager,public}
	# mount /dev/new_add_vg/lv_document /mnt/lv_document
	# mount /dev/new_add_vg/lv_public /mnt/lv_public
	# mount /dev/new_add_vg/lv_manager /mnt/lv_manager

Permanent mounting(with rw changed to defaults):
	# cat /etc/mtab
	# vim /etc/fstab

Check for fstab entry before restart:
	# mount -av


## How to Extend Volume Group and Reduce Logical Volume


