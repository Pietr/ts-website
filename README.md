# ts-website

![Website screenshot](http://i.imgur.com/gKZezVc.png)

**ts-website - free website for your TeamSpeak 3 server**<br>

#### Useful links
- [Demo](https://ts.wruczek.top/)
- [Download](https://github.com/Wruczek/ts-website/archive/master.zip)
- [Report Issues](https://github.com/Wruczek/ts-website/issues/new)
- Contact the author: wruczekk@gmail.com (english or polish)

#### Main Features
- News page, dynamic server status, admin list with status, server viewer, ban list and rules page
- Multiple languages with auto-detection for default language
- PHP 7.0, Apache 2 and nginx support
- Modern and responsive design
- Caching [WIP]
- Free, Open source, under MIT license

### Requirements
PHP Installation:
- PHP 5.5 or newer (although latest PHP version is highly recommended!)
- Installed and enabled ``mbstring`` extension

Recommended nginx configuration:
 - Up-to-date nginx server
 - ``enablehta`` in config.php set to ``true``
 - nginx config set to the following: (**Remember that you need to adjust this config to suit your server!**)
 ````
 server {
 	listen 80 default_server;
 	listen [::]:80 default_server;
 
 	root /var/www/html;
 
 	# Add index.php to the list if you are using PHP
 	index index.php index.html index.htm;
 
 	server_name _;
 
 	location / {
 		# First attempt to serve request as file, then
 		# as directory, then fall back to displaying a 404.
 		try_files $uri $uri/ $uri.html $uri.php$is_args$query_string;
 	}
 
 	# pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
 	
 	location ~ \.php$ {
 		include snippets/fastcgi-php.conf;
 	
 		# With php7.0-cgi alone:
 		#fastcgi_pass 127.0.0.1:9000;
 		# With php7.0-fpm:
 		fastcgi_pass unix:/run/php/php7.0-fpm.sock;
 	}
 
 	 #deny access to .htaccess files, if Apache's document root
 	 #concurs with nginx's one
 	location ~ /\.ht {
 		deny all;
 	}
 
 	#error pages - REMEBER TO CHANGE THE PATH!
 	error_page 403 /path_to_ts-website_please_change_me/errorpages/403.html;
 	error_page 404 /path_to_ts-website_please_change_me/errorpages/404.html;
 	error_page 500 502 503 504 /path_to_ts-website_please_change_me/errorpages/500.html;
 }
 ````

Recommended Apache configuration:
 - Up-to-date Apache server
 - Enabled mod_rewrite (``sudo a2enmod rewrite && service apache2 reload``)
 - Enabled support of htaccess
 - ``enablehta`` in config.php set to ``true``

**If you experience any problems, make sure that directory ``/var/www`` is writeable.**

<br><br>
<p align="center">
<a href="https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=9PL5J7ULZQYJQ" target="_blank"><img src="https://i.imgur.com/s1u7rju.png?1"></a>
</p>
