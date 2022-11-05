# Processes

### Process management 
<pre> ps aux </pre>
In tree format
<pre>
  ps faux  
</pre>

### To see processes + their niceness value 
<pre> 
ps lax 
# to set a nice value to a process
renice -n val PID   # only root can assign a negative nice value 
</pre>

### Signals 
<pre>
# to send a KILL signal to a process 
kill -SIGKILL 1147
# get PID of a process
pgrep -a <process>
# kill by PID
kill -SIGHUP PID
# kill by process name 
pkill -HUP bash 
</pre> 

### backgrounding and foregrounding a process 
<pre>
#foregrounding 
fg 
#backgrounding 
sleep 300 &
</pre>

### processes running in the current terminal 
<pre>
jobs 
</pre>
### currently open files & directories 
<pre>
lsof -p pid
lsof "path_to_process"  // foe exp /bin/sudo 
</pre>

# Analyzing system log files 

Logging daemons collect, store and organize log files 

<pre>
ls /var/log/
grep -r 'ssh' /var/log/
less /var/log/secure   # logs related to secure authentication and authorization ( who gets root permissions , what app requested  privileges ... ) 
</pre>

to check logs in realtime 
<pre>
tail -F /var/log/secure 
</pre>

Journalctl : used to navigate easier through the logs 
<pre>
journalctl 'absolute path of the command' 
journalctl -u sshd.service  # by service name 

# filter by type of log message ( info ,warning, err, crit ) 
journalctl -p err 
journalctl -p info -g '^b' 

# filter by time of the log message 
journalctl -S 02:00 
journalctl -S 01:00 -U 04:00 
</pre>
















































































































































