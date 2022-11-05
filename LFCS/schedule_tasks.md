If we wanna schedule tasks to run at specific time in our linux system we can use :
* Cron : to schedule a job at a specific time ( for exp, every friday at 2 pm )  
* Anacron : to run at a specified time *after system boot* 
* At : to schedule a job only once


# CRON:
to check syntax to use for cron jobs: $cat /etc/crontab 
<pre>
 min  hr  day_of_month  month  day_of_week  TASK
</pre>
* " * " means match all possible values ( i.e every hour ) 
* " , " means match multiple values ( i.e 15,45 ) 
* " - " means range of values ( 2-4 ) [ run the job at 2am, 3am and 4am ]
* " / " means specifies steps ( i.e */4 ) [ run the job every 4 hours ]

35 6 * * * /<full path to a command> 

### to edit a cron table of a user:
<pre>
sudo crontab -e -u nouha 
</pre>

daily = /etc/cron.daily/  
hourly = /etc/cron.hourly/ 

### to add a job:
 <pre>
sudo cp shellscript /etc/cron.hourly 
sudo chmod +rx /etc/cron.hourly/shellscript 
</pre>
### to remove it:
<pre>
sudo rm /etc/cron.hourly/shellscript 
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
used to execute jobs/tasks only once 
<pre>
at 15:00 /<full path to cmd> 
at  'August 20 2022' 
at   'now + 30 minutes' 

# to see the pending jobs 
at -l 
sudo atq  # to see pending jobs for all users 

# to remove a scheduled job
atrm 'nb of the job'   # we use $atq to identify the nb of the job 

# to restrict users who can use at command, we edit these 2 files 
/etc/at.deny 
/etc/at.allow 

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
<pre> 
at '15:30 August 20 2024' /usr/bin/touch atscheduler 
</pre>

then press ctrl+D 

### to add a cron for root user:
<pre>
crontab -e 
</pre>

## Notes about crontab file:
There are 2 methods of writing cron jobs:
* we can either write cron jobs inside /etc/cron.d directory by creating a new file and writing the command in it or by writing directly inside the /etc/crontab file 
* writing directly into /etc/crontab file is not recommended because this file is likely to be overwritten during system upgrades and my commands will be lost 

purpose of crontab:  executing the scripts within /cron.*  directories 
each user has its own crontab file to play with ( different from the one /etc/crontab ‘ system-wide crontab ‘ ) => to see and edit it, run: $ crontab -e 

