BACKUP & RESTORE
----------------

* To find the folder were we want to take backup the folder or file,we use 
 .du -h /etc

* To take the backup for the folder or file we can
 .tar -cvf /backup/read.md /etc
   .backup => folder/directory
   .read.md => name of the backup
   .etc => stored data

 * we use 
  .ls
     read.md
  
  .du -h read.md
     30m  read.md
* compressing the data by using 'gzip'
  .gzip read.md 
    .ls
     7.4M    read.md.gz

* uncompressing the data by using 'gunzip'
    .gunzip read.md.gz
    .ls
    .du -h read.md
      30m read.md

* To extract the data we use,
     .tar -xvf read.md 
      etc  read.md
     .du -h etc |tail -l
       16K     etc/mcelog/triggers
20K     etc/mcelog
0       etc/microcode_ctl/ucode_with_caveats
0       etc/microcode_ctl
0       etc/smartmontools/smartd_warning.d
16K     etc/smartmontools
0       etc/qemu-ga/fsfreeze-hook.d
4.0K    etc/qemu-ga
8.0K    etc/nvme
33M     etc

* back and together gzip
  .tar -zcvf /backup/read.tmd /etc
  .ls 
    etc  read.md.gz  ream.tmd
  .du -h read .tmd.gz
    7.4m  read.tmd

* after back and gzip together we extract
  .tar -zxvf read.tmd
   .du -h read.md.gz
      7.4M    read.md.gz

    
 

