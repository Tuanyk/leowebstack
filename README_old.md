
This is LEMP Stack, containerize with docker for better maintain and upgrade, better security

docker compose up -d and your environment is set!

How to use:

1, Change your password for mysql in docker-compose.yml: environment part, change ADMIN_PASSWORD_HERE and PASSWORD_HERE
2, Create root folder for website, inside web folder, then change the path in the nginx config file at nginx/conf.d/CONFIG_FILE.conf
You will see this line: root /var/web/kynguyencongnghe.com;
Change it to your true path

And change these lines to match your website (kynguyencongnghe.com -> yourwebsite.com):

    server_name kynguyencongnghe.com www.kynguyencongnghe.com;
    access_log /var/log/nginx/kynguyencongnghe.com.access.log;
    error_log /var/log/nginx/kynguyencongnghe.com.error.log;

Consider that, the file kynguyencongnghe.com.conf is for website that use flexible SSL from cloudflare, and you dont need to config anything

If you want to generate your own ssl certificate, please check the config sample file: ssl.example.com.conf, just change the domain name inside the file, generate your certificate by certbot (already installed in the docker container) -> change the ssl certificate path.
Or, you can use python3-certbot-nginx tool, to auto generate / renew ssl certificate. I dont use it because I want to fully control the process, and know how it is processing.

3, Your website code is inside the web/YOURWEBSITE folder. You can use php or wordpress as you want

4, You can update the php version, nginx version, mysql version, everything, it's simple and secure, lossless data with docker.
5, You can increase the limit upload file size as your need, but I set it to 4M or 8M because it's a safe number.
6, The PHP container, I already installed some tools for Wordpress to fully capable of processing images, so if you check the health information of your site, it's good !