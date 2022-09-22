# CRON:
to check syntax to use for cron jobs: $cat /etc/crontab 

* " * " means match all possible values ( i.e every hour ) 
* " , " means match multiple values ( i.e 15,45 ) 
* " - " means range of values ( 2-4 ) [ run the job at 2am, 3am and 4am ]
* " / " means specifies steps ( i.e */4 ) [ run the job every 4 hours ]

35 6 * * * /<full path to a command> 

### to edit a cron table of a user:
$ sudo crontab -e -u nouha 

daily = /etc/cron.daily/
  
hourly = /etc/cron.hourly/ 

### to add a job:
 <pre>
$ sudo cp shellscript /etc/cron.hourly 
$ sudo chmod +rx /etc/cron.hourly/shellscript 
</pre>
### to remove it:
<pre>
$ sudo rm /etc/cron.hourly/shellscript 
</pre>
  
# ANACRON
  
It is used to schedule operations to run at a set time after each system boot 
( useful if you need to do some commands but not certain that your computer will be powered on at any given time during the day ) 

syntax:
<pre>
#period_in_days   #delay_in_mins  #job_identifier   #command 

@weekly             <nb>            test_job          /<absolute_path_to_the_command> 
<nb>                                cron.daily            
@monthly 
________________________________________________________________________________________
for example: 
1                      10         <job_identifier>         /script.sh 

=> the command above runs the script no more than once a day, 10 mins after system boot 

</pre>

# AT 
<pre>
at 15:00 /<full path to cmd> 
at  'August 20 2022' 
at   'now + 30 minutes' 
</pre>

### to force anacron to run all jobs:
<pre>
$ sudo anacron -n -f 
</pre>
### to identify the currently scheduled jobs:
<pre>
$ atq 
</pre>

Using root user, schedule below given command to run at 15:30 August 20 2024 by using at utility:
  
$ at '15:30 August 20 2024' /usr/bin/touch atscheduler 

then press ctrl+D 

### to add a cron for root user:
$ crontab -e 
