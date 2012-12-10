check_rss
=========


First version taken from http://john.wesorick.com/2011/10/nagios-plugin-checkrss.html


 Added 
------

 - Support for empty feed
 - global clean up, pylint and pep8 almost silent



Usage 
-----

Pick a rss feed from your provider :

 * Amazon - http://status.aws.amazon.com/
 * Google - http://www.google.com/appsstatus


Copy check_rss.py into your plugins directory 
'$USER1$' in /etc/nagios/private/resource.cfg


- - - 

### Amazon 

Example :
  check_rss.py -T 1  http://status.aws.amazon.com/rss/s3-us-west-2.rss

Get service list from : 
  curl -s http://status.aws.amazon.com | grep rss | cut -d '"' -f 4

     define command{
         command_name  check_aws_status
         command_line  $USER1$/check_rss.py -H http://status.aws.amazon.com/rss/$ARG1$.rss -T $ARG2
      }

     define service{
          use                   generic-service
          service_description   status s3-us-west-2
          check_command         check_aws_status!s3-us-west-2!1
          host_name             localhost
      }
      
- - -

### Google apps

     define command{
         command_name  check_google_apps_status
         command_line  $USER1$/check_rss.py -H http://www.google.com/appsstatus/rss/en -T $ARG1
     }

     define service{
         use                   generic-service
         service_description   google apps status 
         check_command         check_google_apps_status!1
         host_name             localhost
    }


