#### Shell Scripting #####

* types of shells
 
 .BSH/sh-->bourne shell
 .bash-->bourne-again
 .csh-->c shell
 .ksh-->korn shell

* check total shells installed
 .echo $SHELLS
 .echo $0

* to change shell for root to normal user
 .grep venu /etc/passwd
 .usermod -s /bin/sh venu
 .grep venu /etc/passwd

* normal user can it change shell
 .chsh
   /bin/sh
   passwd:xxxx
 .grep venu /etc/passwd


