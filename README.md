hard-drive-forensic-imaging# Hard Drive to USB Forensic Imaging

Creating a forensic disk image (.img) of a hard drive 
using dcfldd on Kali Linux.

 Tools Used
- Kali Linux
- dcfldd (forensic version of dd)
- inland USB-A/USB-C to SATA adapter
- GNOME Disks utility

Key Concepts
- Formatted target USB as NTFS to avoid the 4GB 
  file size limit of FAT32
- Used dcfldd for forensic-grade imaging with 
  status output
- Proper mount/unmount procedure to avoid 
  data corruption

 Process
1. Connect hard drive via SATA adapter
2. Format target USB as NTFS
3. Identify drives with: lsblk -o NAME,SIZE,MODEL,MOUNTPOINT
4. Create mount point: sudo mkdir -p /mnt/evidence_usb
5. Mount USB: sudo mount /dev/sdX /mnt/evidence_usb
6. Image the drive: 
   sudo dcfldd if=/dev/sdX of=/mnt/evidence_usb/evidence.img bs=1M status=on
7. Unmount cleanly: sudo umount /dev/sdX /mnt/evidence_usb

 Notes
- dcfldd can wipe a drive if input/output are reversed — 
  always verify device names with lsblk first
- Imaging can take hours depending on drive size
- Disabled screensaver to prevent interruption during transfer
