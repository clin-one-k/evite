Evite Deploy Instruction
========================
It requires php 5.4 because the code is using
$var = [], which only allowed in 5.4. In 5.3, it should be $var = array();

update to 5.4 see http://askubuntu.com/questions/343560/update-server-php-version-to-5-4-10-via-the-command-line
1. Have file degevite-2013-01-16.tar.gz and degevite-2013-01-16.sql
2. Unzip degevite-2013-01-16.tar.gz and you get deg-evite folder.
3. Place deg-evite folder in /var/www
4. Because there are links files that is hard-coded to this directories so do not change.
5. Hard-coded link file is at web/bundels
6. Start apache and go to DOMAIN/deg-evite/web/app_dev.php/admin/event/list
You should see "probidden" because it is been locked.
7. Open editor and common out line 2 "die('forbidden');" on web/app_dev.php
8. Now you should be asked username and password, if you have a unexpected "[" error, you are running php 5.3
9. go to app/config/security.yml line 25 "pattern:    ^/admin", change to "pattern:    ^/adminx " so it won't require password for admin
now you get sql cannot access error.
Edit app/config/parameters.yml line 6 and 7 to update the sql username and password, now you will see error Unknown database 'degevite'
Create database degevite and execute degevite-2013-01-16.sql, but skip line 85 and after.
Now you should be able to see the page.

Make sure on /web/tickets has write permission so the ticket image can be written.
