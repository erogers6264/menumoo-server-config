# Configuring a Linux Web Server

## Access Information:
- ~~IP address: 52.36.239.162~~
- ~~SSH port: 2200~~
- ~~URL: http://ec2-52-36-239-162.us-west-2.compute.amazonaws.com/~~
Note: The Amazon EC2 instance containing the configured web server has been removed since completing the Full Stack Nanodegree on July 31st, 2016

## Summary of configuration changes
- To secure this VPS, I first created a new user `grader`, granted `grader`
sudo permissions, and disabled remote login as root on the server.
- I made the rest of the changes as `grader` using the `sudo` command.
- I ran `sudo apt-get update && sudo apt-get upgrade` to update the currently
installed packages.
- To change the SSH port from 22 to 2200, I edited the file `/etc/ssh/sshd_config`
- I configured the Uncomplicated Firewall to only allow incoming connections for
SSH (port 2200), HTTP (port 80), and NTP (port 123).
```shell
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 2200/tcp
sudo ufw allow www
sudo ufw allow ntp
sudo ufw enable
sudo ufw status
```
- The server was already configured to the UTC timezone.
- Disallowed http access of the .git folder.

## Summary of software installation
- Apache2 web server and wsgi_mod so it can interface with Python.
  - Created a wsgi script for menumoo and configured a new virtual host for
  Apache.
- emacs24 to use as my terminal based text editor (it's fantastic).
- python-pip to install Python packages.
- Using pip, I installed all the dependencies of my application.
  - flask, flask-sqlalchemy, flask-wtforms, psycopg2, requests, oauth2client,
  oauth, itsdangerous, httplib2
- PostgreSQL
- Got to have git

## Sources used
### Linux
- <http://askubuntu.com/questions/168280/how-do-i-grant-sudo-privileges-to-an-existing-user>
- <http://askubuntu.com/questions/59458/error-message-when-i-run-sudo-unable-to-resolve-host-none>
- <http://askubuntu.com/questions/27559/how-do-i-disable-remote-ssh-login-as-root-from-a-server>
- <http://askubuntu.com/questions/36785/tail-how-to-quit-tail-and-restore-terminal-window>

### SSH
- <https://wiki.archlinux.org/index.php/Secure_Shell>
- <https://wiki.archlinux.org/index.php/SSH_keys>
- <http://www.liquidweb.com/kb/changing-the-ssh-port/>
- <http://stackoverflow.com/questions/6394762/how-to-setup-ssh-access-for-amazon-ec2-instance>

### Apache
- <http://httpd.apache.org/docs/2.4/>
- <http://httpd.apache.org/docs/2.4/getting-started.html>
- <https://httpd.apache.org/docs/1.3/logs.html>
- <http://modwsgi.readthedocs.io/en/develop/user-guides/quick-configuration-guide.html>
- <http://askubuntu.com/questions/258901/warning-documentroot-x-does-not-exist-when-starting-apache2>
- <http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html>
- <http://stackoverflow.com/questions/14410455/setting-up-python-with-wsgi-on-apache-for-a-directory>
- <http://modwsgi.readthedocs.io/en/develop/user-guides/reloading-source-code.html>
- <http://stackoverflow.com/questions/4731364/internal-error-500-apache-but-nothing-in-the-logs>
- <https://code.google.com/archive/p/modwsgi/>

### PostgreSQL
- <https://help.ubuntu.com/community/PostgreSQL>
- <http://packages.ubuntu.com/trusty/database/postgresql>
- <http://dba.stackexchange.com/questions/1285/how-do-i-list-all-databases-and-tables-using-psql/34419>
- <https://www.digitalocean.com/community/tutorials/how-to-secure-postgresql-on-an-ubuntu-vps>
- <http://killtheyak.com/use-postgresql-with-django-flask/>

### OAuth
- <https://discussions.udacity.com/t/lesson-4-facebook-login-not-working/27869>
- <https://developers.google.com/api-client-library/python/guide/aaa_client_secrets>
- <https://developers.facebook.com/docs/javascript/advanced-setup>

### Flask
- <http://flask.pocoo.org/docs/0.11/deploying/>
- <http://flask.pocoo.org/docs/0.11/deploying/mod_wsgi/>

### Emacs
- <https://www.gnu.org/software/emacs/manual/html_node/emacs/Save-Commands.html>
- <https://www.emacswiki.org/emacs/CategorySearchAndReplace>

### General
- <https://discussions.udacity.com/t/p5-how-i-got-through-it/15342>
- <https://discussions.udacity.com/t/markedly-underwhelming-and-potentially-wrong-resource-list-for-p5/8587>
- <https://en.wikipedia.org/wiki/Virtual_hosting>
- <https://github.com/stueken/FSND-P5_Linux-Server-Configuration>
- <https://github.com/SteveWooding/fullstack-nanodegree-linux-server-config>
- <http://simplejson.readthedocs.io/en/latest/>
- <https://realpython.com/blog/python/kickstarting-flask-on-ubuntu-setup-and-deployment/>
- <http://blog.udacity.com/2015/03/step-by-step-guide-install-lamp-linux-apache-mysql-python-ubuntu.html>
- <https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu>
- <https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps>
- <https://daringfireball.net/projects/markdown/syntax>
- <https://www.python.org/dev/peps/pep-0333/>



