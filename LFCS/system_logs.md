logging daemons collect/organize and store logs 
exp : rsyslog 

$ ls /var/log/ 

to search for log files of a specific svc ( ssh for exp ):
$ grep -r 'ssh' /var/log/  

logs related to secure auth and authz:
$ less /var/log/secure :
it shows: 
- who used sudo to get root permissions, what app requested privileges and what it did with them ..)  
- exact time when it happened, the src/app that generated the log msg, the log msgs itself   

$ less /var/log/messages


to look at logs in realtime: ( use -F : follow mode ) 
$ tail -F /var/log/secure 

to navigate easier thru the logs:
$ journalctl <absolute path of the command>

exp: $ journalctl /bin/sudo 
     $ journalctl -u sshd.service   ( -u : unit ) 
     
types of log messages in journalctl: 
- info 
- warning 
- err 
- crit 

$ journalctl -p err 
$ journalctl -p info -g '^b'  ( filter out  'info' logs that have msgs beginning with 'b' or 'B' ) 
$ journalctl -S 02:00 ( filter out logs starting after 2 am ) 
$ journalctl -S 01:00 -U 04:00 

$ last
$ lastlog  ( shows when each user has logged in  )

to look thru multiple files inside a specific directory:
$ sudo grep -r 'reboot' /var/log/ > reboot.log

