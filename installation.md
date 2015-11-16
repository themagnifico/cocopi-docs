Installation
===

To get started, download a Cocopi package that comes with some sample content.  
Installing Cocopi is as easy as dropping the downloaded folder in the desired location of your PHP 5.4+ ready web server. That's it. No database setup or installer is needed.

For example, extract the package to a `cocopi` folder in your web server documents directoy. In your browser, open `http://localhost/cocopi` or `example.com/cocopi` to see your site.

Cocopi comes with an admin panel located in the `cockpit/` folder, so for example at `example.com/cocopi/cockpit`. Before you login to Cockpit for the first time, run the installation at `example.com/cocopi/cockpit/install`.

## Requirements

PHP 5.4+

## Apache 2

Place the `cocopi` folder in your `htdocs` directory. Done.

## nginx

Place the `cocopi` folder in your `html` directory. Depending on your server setup, that might have been it already.

If it doesn't work out of the box, try a nginx site configuration like the following.

```
server {
    listen 80 default_server;
    listen [::]:80 default_server ipv6only=on;

    root /usr/share/nginx/html;
    index index.php index.html index.htm;

    # Make site accessible from http://localhost/
    server_name localhost;

    location / {
        # First attempt to serve request as file, then
        # as directory, then fall back to displaying a 404.
        try_files $uri $uri/ /index.php;
    }

    error_page 404 /404.html;
    error_page 500 502 503 504 /50x.html;
    location = /50x.html {
        root /usr/share/nginx/html;
    }

    location ~ \.php$ {
        try_files $uri =404;
        fastcgi_split_path_info ^(.+\.php)(/.+)$;
        fastcgi_pass unix:/var/run/php5-fpm.sock;
        fastcgi_index index.php;
        include fastcgi_params;
    }

    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    location ~ \.php$ {
        fastcgi_split_path_info ^(.+\.php)(/.+)$;

    #   # With php5-fpm:
        fastcgi_pass unix:/var/run/php5-fpm.sock;
        fastcgi_index index.php;
        include fastcgi_params;
    }

}

```
