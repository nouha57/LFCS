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

# Logs















































































































































