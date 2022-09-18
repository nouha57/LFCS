# Processes

## Process management 
ps aux
  ## tree format
  ps faux  

## TO see processes + their niceness value 
ps lax 
  ### to set a nice value to a process
  renice -n <val> <PID>
  // only root can assign a negative nice value 

## Signals 
  ## get PID of a process
  pgrep -a <process>
  ## kill by PID
  kill -SIGHUP <PID>
  ## kill by process name 
  pkill -HUP bash 

## backgrounding and foregrounding a process 
  ## foregrounding 
  fg 
  ## backgrounding 
  sleep 300 &
  ## processes running in the current terminal 
  jobs 
  ## currently open files & directories 
  lsof -p <pid>
  sudo lsof <path_to_process>  // foe exp /bin/sudo 


# Logs















































































































































