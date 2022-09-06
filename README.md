# boyolangu-tulungagung.github.io

# Setting for Apache Server Based

enable ae2nwrite

in /etc/apache2/sites-available/000-default.conf add this settings for a full redirect

```
<Directory /path-to-dir>
    Options Indexes FollowSymLinks MultiViews
    AllowOverride All
    Require All granted
</Directory>
```

in directory structure

```
<IfModule mod_rewrite.c>
	RewriteEngine On
	RewriteBase /

	RewriteCond %{REQUEST_FILENAME} !-f
	RewriteCond %{REQUEST_FILENAME} !-d
	RewriteCond %{REQUEST_FILENAME} !-l
	
	RewriteRule ^ index.html [L]
</IfModule>
```

# Setting for Nginx Server Based

```
server {
    listen port;
    listen [::]:82;

    server_name _;

    root /path-to-dir;
    index index.html

    location / {
        try_files $uri /index.html
    }
}
```