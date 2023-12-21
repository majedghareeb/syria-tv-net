# syria-tv-net
Step By Step | Wordpress multisite using LocalWP and Bedrock

- Install Wordpress on localWP
- Navigate to app folder using shell and git clone git@github.com:majedghareeb/syria-tv-net.git
- Run composer install 

WP_ENV='production'


token: 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

Htaccess content
RewriteEngine on
RewriteCond %{HTTP_HOST} ^beta.syria-tv.net$ [NC,OR]
RewriteCond %{HTTP_HOST} ^www.beta.syria-tv.net$
RewriteCond %{REQUEST_URI} !web/
RewriteRule (.*) /web/$1 [L]

# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
RewriteBase /web/wp/
RewriteRule ^index\.php$ - [L]

# add a trailing slash to /wp-admin
RewriteRule ^([_0-9a-zA-Z-]+/)?wp-admin$ $1wp-admin/ [R=301,L]

RewriteCond %{REQUEST_FILENAME} -f [OR]
RewriteCond %{REQUEST_FILENAME} -d
RewriteRule ^ - [L]
RewriteRule ^([_0-9a-zA-Z-]+/)?(wp-(content|admin|includes).*) $2 [L]
RewriteRule ^([_0-9a-zA-Z-]+/)?(.*\.php)$ $2 [L]
RewriteRule . index.php [L]
</IfModule>
# END WordPress
# php -- BEGIN cPanel-generated handler, do not edit
# Set the “ea-php81” package as the default “PHP” programming language.
<IfModule mime_module>
  AddHandler application/x-httpd-ea-php81 .php .php8 .phtml
</IfModule>
# php -- END cPanel-generated handler, do not edit