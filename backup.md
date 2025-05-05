### BACKUP & RESTORE


* find the folder were we want to take a backup & create a name backup file and name of back `file_name`

* du -h /etc (shows how much size of file)

 ![preview](images/backup1.PNG)
  
*  take the backup for the folder
 
* tar -cvf /backup/read.md /etc
 .c=>copy
 .v=>verbs
 .f=>file
 
 ![preview](images/back23.PNG)

* backup => folder/directory
* etc.tar=> name of create a backup folder 
* etc => stored data
* cd /backup
   
* inside the directory we can take the backup

 ![preview](images/back24.PNG)

* compressing the data by using `gzip` command 

* uncompressing the data by using `gunzip` to `gzip` command 
 
* du -h etc.tar.gz
 
 ![preview](images/back25.PNG) 

* gzip etc.tar (gzip means actually orignal data to compress less size )
 
 ![preview](images/back26.PNG)

 ![preview](images/back27.PNG)

* gunzip (the data having actual size)
 
 ![preview](images/back28.PNG)

* extrating the data and backup

 ![preview](images/back28.PNG)

* take backup together and gzip

* tar -zcvf /backup/etc.tgz /etc/ |tail -5
 
![preview](images/back29.PNG)

* extra the data for each create a file

![preview](images/back30.PNG)

* take a backup to generate another folder

* tar -xvf etc.tar <backup_floder>




 
 
     


    
 

