# CRON:
to check syntax to use for cron jobs: $cat /etc/crontab 

* " * " means match all possible values ( i.e every hour ) 
* " , " means match multiple values ( i.e 15,45 ) 
* " - " means range of values ( 2-4 ) [ run the job at 2am, 3am and 4am ]
* " / " means specifies staps ( i.e */4 ) [ run the job every 4 hours ]

35 6 * * * /<full path to a command> 

### to edit a cron table of a user:
$ sudo crontab -e -u nouha 

daily = /etc/cron.daily/
  
hourly = /etc/cron.hourly/ 

### to add a job:
$ sudo cp shellscript /etc/cron.hourly 
$ sudo chmod +rx /etc/cron.hourly/shellscript 
###to remove it:
$ sudo rm /etc/cron.hourly/shellscript 

# ANACRON
syntax:
<pre>
#period_in_days   #delay_in_mins  #job_identifier   #command 

@weekly             <nb>            test_job          /<absolute_path_to_the_command> 
<nb>                                cron.daily            
@monthly 
</pre>

# AT 
at 15:00 /<full path to cmd> 
at  'August 20 2022' 
at   'now + 30 minutes' 


### to force anacron to run all jobs:
$ sudo anacron -n -f 

### to identify the currently scheduled jobs:
$ atq 

Using root user, schedule below given command to run at 15:30 August 20 2024 by using at utility:
  
$ at '15:30 August 20 2024' /usr/bin/touch atscheduler 

then press ctrl+D 

### to add a cron for root user:
$ crontab -e 
