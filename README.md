

First version taken from http://john.wesorick.com/2011/10/nagios-plugin-checkrss.html


 Added 
 =====

 - Support for empty feed
 - global clean up, pylint and pep8 almost silent



Usage 
=====

Pick a rss feed from your provider :

 * Amazon - http://status.aws.amazon.com/
 * Google - http://www.google.com/appsstatus/rss/en


check_rss.py -T 1  http://status.aws.amazon.com/rss/s3-us-west-2.rss


In nagios 

define command

define service check_rss!s3-us-west-2
