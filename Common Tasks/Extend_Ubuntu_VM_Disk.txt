Proxmox

Select the Servername (in Server View), then select "Hardware" in the main tab, select "Hard Disk (sata0)" then click "Resize Disk" and increase size as desired, then click "Resize Disk"
use 'fdisk -l' to find <diskmountpoint>, like /dev/sda
use 'fdisk <diskmountpoint>' to create a new partition <newpartition> (like /dev/sda3) of type LVM
use 'vgdisplay' to get your <volumegroupname>
use 'vgextend -l+100%FREE <volumegroupname> <newpartition>' to extend the volume group to the new partition
use 'lvdisplay' to display your <logicalvolumename>, like /dev/mapper/<volumegroupname>-root
use 'resize2fs <logicalvolumename>' to extend the volume to fill the space
