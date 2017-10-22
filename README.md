# Note

Migrated and merged with [https://github.com/pothi/wordpress-nginx/](https://github.com/pothi/wordpress-nginx/).

# WordPress-Nginx

WordPress specific Nginx configurations, tweaks, compatibility routines, etc.

## Compatibility

Tested in Debian 8+ and Ubuntu 16.04+

## How to Install

Please backup your old configuration files...

```bash
TIMESTAMP=$(date +%F_%H-%M-%S)
mkdir $HOME/backups &> /dev/null
cp -a /etc/nginx $HOME/backups/etc-nginx-$TIMESTAMP
```

As __sudo or root__, please use the following guidelines...
```bash
service nginx stop

git clone https://github.com/pothi/wp-nginx-deb.git ~/git/wp-nginx-deb
cd ~/git/wp-nginx-deb
cp -a conf.d/ globals/ sites-available /etc/nginx

# Other steps that depends on your particular requirement:
# YOUR_DOMAIN_NAME=tinywp.com
# mv /etc/nginx/sites-available/domainname.conf /etc/nginx/sites-available/$YOUR_DOMAIN_NAME.conf
# cd /etc/nginx/sites-enabled/
# ln -s ../sites-available/$YOUR_DOMAIN_NAME.conf
# sed -i --follow-symlinks 's/domainname.com/'$YOUR_DOMAIN_NAME'/g' /etc/nginx/sites-enabled/$YOUR_DOMAIN_NAME.conf

nginx -t && service nginx start
```

## Questions, Issues or Bugs?

+ Please submit issues or bugs via Github
+ Patches, improvements, and suggestions are welcomed.
+ Please use contact form at https://www.tinywp.in/contact/ , if you'd like to contact Pothi Kalimuthu for other reasons.
+ I'm available for hire to setup, tweak or troubleshoot your server to provide *the fastest WordPress hosting*.
+ Thanks for having a look here. Have a good time!

## TODO

+ find the number of cores and insert them as worker_processes
+ find the port (or socket) from php-fpm config and insert it in lb.conf
