## MANAGING PROCESS
 any activity to run in system is known as `process`

* 1.interactive process:we can interact the process `read,write,copy,delete`
  2.system process:
  3.automatic process:automatically starts like `date,time,month`
* parent process:every process as a parent process except systemd
  child process:

  .tty
    /dev/pts/0

* .ps -a

* check the kill signals for process
 .kill -l     
* check the process for normal user
 .ps -U <username>

*  check the group pid 
 .ps -G <groupname>

*  status of a process
 .ps -elf |more

* sleeping process
 . ps -elf |grep -w sleep

* running process
 .ps -elf |grep -w R

* zambi process
 .ps -elf |grep -w z (nothing but parent is killed still child running)

* kill the process
 .kill -9 <pid>
 .kill -15 (termination)

* priority:importance,perfernances
   lower the value & higher the priority
   higher the priority & lower the value
   nice range b/w -20 to 20

* to change the nice value  
* login into new session as a root
  .nice -n 5 cat >hello
  .ps -elf |grep cat

 * to change the renice value
  .renice -8 6064 


 
 ## Monitoring commands 
 1.cpu
 2.memory
 3.i/o
 4.network

 1.cpu
 . cat /proc/cpuinfo
 .ls cpuinfo
 . sar
 .systemctl status systat
 .systemctl starts systat
 .sar 1 4

 2.memory 
  .cat /proc/meminfo
  .vmstat
  .vmstat -s
  .vmstat 1 4

  3.i/o
   .iostat -d sda3
   .iostat -d sda4

  4. network
    .netstat -nr
    .netstat -i

  5.top 
 * see the cpu utilization
    h-->help
    b-->running process
    z-->colour
    l-->search
    r-->change the nice value
    k-->kill the sidnal   
 