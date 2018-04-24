## Proxmox resize Ubuntu VM disk size

1. In Proxmox Server View, select the Servername to expose your list of VMs, then select the name of the VM you want to update, then select *Hardware* in the main tab, select *Hard Disk (sata0)*, then click *Resize Disk* and increase size as desired, finally click *Resize Disk* to extend the space alloted to the VM

1. login to your VM with SSH or the proxmox VNC console

1. input *fdisk -l* to find `<diskmountpoint>` which should look like */dev/sda*
  
1. input *fdisk `<diskmountpoint>`* to create a new partition `<newpartitionname>` of type LVM
  
1. input *vgdisplay* to get your `<volumegroupname>`
  
1. input *vgextend -l+100%FREE `<volumegroupname> <newpartition`* to extend the volume group to include the new partition
  
1. input *lvdisplay* to display your `<logicalvolumename>` which should look like */dev/mapper/volumegroupname-root*
  
1. input *resize2fs `<logicalvolumename>`* to extend the volume to fill the space
