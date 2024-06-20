
# LEMP Stack with Docker

This project sets up a LEMP stack (Linux, Nginx, MySQL, PHP) containerized with Docker for better maintainability, upgrades, and security.

## Quick Start

To get your environment up and running, simply execute:

```sh
docker-compose up -d
```

## How to Use

### 1. Change MySQL Password

Edit the `docker-compose.yml` file and update the MySQL passwords in the `environment` section:
```yaml
environment:
  MYSQL_ROOT_PASSWORD: ADMIN_PASSWORD_HERE
  MYSQL_PASSWORD: PASSWORD_HERE
```

### 2. Configure Nginx

- Create a root folder for your website inside the `web` folder.
- Update the path in the Nginx configuration file (`nginx/conf.d/CONFIG_FILE.conf`):

  ```nginx
  root /var/web/yourwebsite.com;
  ```

- Modify the following lines to match your website domain (replace `yourwebsite.com`):

  ```nginx
  server_name yourwebsite.com www.yourwebsite.com;
  access_log /var/log/nginx/yourwebsite.com.access.log;
  error_log /var/log/nginx/yourwebsite.com.error.log;
  ```

#### Flexible SSL with Cloudflare

If you are using Cloudflare's flexible SSL, no additional configuration is needed. The provided `kynguyencongnghe.com.conf` file is pre-configured for this setup.

#### Generating Your Own SSL Certificate

To generate your own SSL certificate:

1. Edit the `ssl.example.com.conf` file and change the domain name.
2. Use Certbot (already installed in the Docker container) to generate your certificate.
3. Update the SSL certificate path in the configuration file.

Alternatively, you can use `python3-certbot-nginx` for automatic SSL certificate generation and renewal. However, manual control is recommended to understand the process.

### 3. Website Code

Place your website code inside the `web/YOURWEBSITE` folder. You can use PHP or WordPress as needed.

### 4. Updating Versions

You can easily update the versions of PHP, Nginx, and MySQL. Docker ensures this process is simple, secure, and data loss-free.

### 5. Upload File Size Limit

You can adjust the file upload size limit based on your requirements. By default, it is set to 4M or 8M, which is a safe limit.

### 6. PHP Container Tools

The PHP container includes tools necessary for WordPress, ensuring your site can fully process images and other media. This helps maintain the health and performance of your website.

---

By following these steps, you'll have a robust and secure LEMP stack environment using Docker. Happy coding!
