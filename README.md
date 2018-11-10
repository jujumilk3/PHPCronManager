# PHPCronManager
#### Preface
I tried to make this as simplest. So There's no handling about some danger commands(e.g : rm -rf \[somethings\], halt, reboot, shutdown, and so on... ).
So I want you to be careful when you use this class. I've no responsibility about problems occurred by using this class.
<br><br>

#### Description
Be made to approach linux's cron system. Cronjobs are made by this class, managed by CRONTAG. 
CRONTAG is a comment that pasted cronjob's tail.

#### Test Environment
OS  : CentOS 6.8 (Final)<br>
php : PHP 7.0.16<br>
And understandably **crond** installed. 
<br><br>

e.g (assume u to load this file completely)<br>
```php
$cron_manager = new CronManager();

$cron_add_result = $cron_manager->add_cronjob('* * * * * date >> /var/testdir/datelog.txt 2>&1', 'datelog');
//if this codes worked normally, u will get array return with success status
//Already listed cronjob doesn't  get removed unlikely command `cronjob -`
//Cronjob added like bellow form
//*****************Already registered cronjobs...********************
//* * * * * * * * * * date >> /var/testdir/datelog.txt 2>&1 #CRONTAG=datelog

$listed_cron = $cron_manager->get_listed_cronjob();
//display only cronjobs except comments and blank lines

$crontab = $cron_manager->get_crontab();
//display like command. `crontab -l`

$cron_duplication_check = $cron_manager->cron_duplication_checker('datelog');
//param is CRONTAG. datelog cron is already registered so this returns bool true.
//It checkes per line, so please crontag




```