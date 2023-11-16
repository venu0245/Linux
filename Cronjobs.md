#####  JOB AUTOMATION ######
* <cat /etc/crontab>

SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root

# For details see man 4 crontabs

# Example of job definition:
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name  command to be executed

* <ls /var/spool/cron>
 .check the whose crontab file used

* <crontab -l>
 . see the list for scheduling the task 
   2 17 07 10 * /cron.sh>/dev/pts/0

* <crontab -e>
 .create a scheduled to run a task for specific timings

* <crontab -r> <name>
 .delete the cron jobs whoever created

* <crontab -lu>
 .see the user's who create the cronjobs 

# Delete the admin user  for normal user create a cron job 
 .crontab -lu -r <username>

# To allow /deny of the <user> 
 .vim /etc/deny
 .vim /etc/allow

*same user on deny/allow file only perfered for allow file 

# To display the scheduled task name of the message on screen using <echo "message">>/dev/pts/0
 .tty
   /dev/pts/0

# sleep 10
* display the print message for to run a task

# To create a script with (.extention) </cron.sh>

#  To take a backup of file /etc folder with directory 

 .vim /cron.sh
   #!/bin/bash (shebang)
      echo "taking backup"
      sleep 5
      tar -cvf /backup/read.md /etc
      echo "backup compeleted"
 .wq!      

 .chmod +x /cron.sh
 .ls -l /cron.sh
 .cat /cron.sh

# add a script in crontab -e file
 .crontab -e
  33 17 10 07 * /cron.sh>/dev/pts/0
 .wq!
 
 .crontab -l
 .date
 .watch /backup  

# create a script with /cron.sh

  #!/bin/bash
  echo "creating a file"
  sleep 10
  touch backup/file1
  echo "created compeleted"
 .wq!

# add the script in <crontab -e> file & sheduled the task
  33 17 10 07 * /cron.sh>/dev/pts/0
 .wq!

* whatever changes in the script add in the <crontab -e> file and sheduled the time zones 

 .(minutes,hours,day,month,day of week)
  
  1=mon
  2=tue
  3=wed
  4=thu
  5=fri
  6=sat
  0/7=sun



 
