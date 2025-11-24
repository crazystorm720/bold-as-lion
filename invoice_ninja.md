# Invoice Ninja Deployment - Primitive Instructions

## Core Requirements
- Debian server
- Domain/IP pointing to server
- Basic Linux command knowledge

## Atomic Steps

**1. Install Dependencies**
```bash
sudo apt update
sudo apt install -y nginx mariadb-server php-fpm php-mysql php-curl php-gd php-xml php-zip php-mbstring unzip
```

**2. Setup Database**
```bash
sudo mysql -e "CREATE DATABASE ninja;"
sudo mysql -e "CREATE USER 'ninja'@'localhost' IDENTIFIED BY 'yourpassword';"
sudo mysql -e "GRANT ALL ON ninja.* TO 'ninja'@'localhost';"
```

**3. Deploy Application**
```bash
cd /var/www
sudo wget https://github.com/invoiceninja/invoiceninja/releases/download/v5.7.11/invoiceninja.zip
sudo unzip invoiceninja.zip
sudo mv invoiceninja-5.7.11 ninja
sudo chown -R www-data:www-data ninja
```

**4. Configure Web Server**
Create `/etc/nginx/sites-available/ninja`:
```
server {
    listen 80;
    server_name your-domain.com;
    root /var/www/ninja/public;
    index index.php;
    
    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }
    
    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php-fpm.sock;
    }
}
```
```bash
sudo ln -s /etc/nginx/sites-available/ninja /etc/nginx/sites-enabled/
sudo nginx -t && sudo systemctl reload nginx
```

**5. Complete Setup**
- Browse to `http://your-domain.com/setup`
- Follow web installer
- Use database credentials from step 2

**6. Enable Background Tasks**
```bash
sudo crontab -u www-data -e
```
Add: `* * * * * cd /var/www/ninja && php artisan schedule:run >> /dev/null 2>&1`

## First Principles
- Web server serves files
- Database stores data  
- PHP processes application logic
- Cron handles scheduled tasks
- File permissions control access

## Documentation
- Invoice Ninja Docs: https://invoiceninja.github.io
- Debian Packages: https://packages.debian.org

This covers the primitive operations needed. Everything else is optimization.
