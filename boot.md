Booting Process:
-----------------

* Changing the booting time of the system

* To check the booting timing in the file
   
   ==>grep -i timeout /boot/grub2/grub.cfg

* To configation file to change the boot time
   
   ==>vim /etc/defaultgrub

* After changing the boot time of the we can update the file
   
   ==>grub2-mkconfg -o /boot/grub2/grub.cfg

* we can check after changing boot time
    ==>grep -i timeout /boot/grub2/grub.cfg

To changing the graphic to command modes:
-----------------------------------------

Login screen: to observe the screen
 1.graphic 
 2 command line

* To check the runlevel for graphic mode or command line mode
  ==>who -r

* Default runlevel
  
  ==>cat /etc/inittab

* To check the type of run level
  
  ==>systemctl get-default          

* To change the runlevel to graphic mod to command line mod
  
  ==>systemctl set-default runlevel3.target (for runlevel3 is command line)
  
  .poweroff to check the terminal
  
  ==>systemctl set-default runlevel5.target (for runlevel5 is graphs mode)
  
  .poweroff to check the terminal
 
 LOST THE ROOT PASSWD:
 ---------------------
  .poweron the machine
* after poweron the machine booting will be starts to press any to stop the booting
  
  .ctrl a (begining of the line)
  .ctrl e (ending of the line)

* press the key 'e'
  and type key ctrl+e for ending of the line  type "rd.break" & "ctrl+x"
  
* to check the mount point rw permission 
  ==>mount
  ==>mount |grep sysroot
* to change the rw permission     
  ==>mount -o remount sysroot -o rw
  ===>mount |grep sysroot

* to convervet the ROOT
 ==>chroot sysroot
   .pwd
 ==>PASSWD
   .enter the new passwd twice after that we run the command 
  ==>touch /.autorelabel
    .exit
    .exit 

TROUBLESHOOT FOR INSTALLING BOOT LOADER :
-----------------------------------------
*if boot loader fails we install the boot loader in dvd(rhel8)

* choose the dvd in the virtual box in setting 
 .poweroff

* To check the details for last  system booting times
 ==>cat /var/log/boot.log

 .Troubleshoot
 .rescure a rhel
  1.continue
  2.read-only mount
  3.skip to shell
  4.quit
* 1.continue
   .enter
   ==>chroot /mnt/sysroot

 * to check the disk boot (*)  
   ==> fdisk -l |more
   ==>grub2-install /dev/sda
   .exit
   .poweroff 
Note:1.if we install boot loader in dvd(rhel8) 
   ==>grub2-install /dev/sda
     2.poweron the machime not working the root passwd when (dvd rhel8 inside )
     3.we uninstall the boot loader in dvd(rhel8)
     4.grub2-uninstall /dev/sda
     5.remove the dvd in virtual box setting
     6.now poweron the machine we login the terminal to connect rhel8
     7.to follow the above steps
     