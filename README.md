# angular-remove-hash-in-apache
how to remove angular hash in web server apache2. 
in default angular initial is not using hash in route.  if you want to set use hash, `RouterModule.forRoot(routes, { useHash: true })` set false to remove hash or delete the property `{ useHash: false }`

add the `.htaccess` in root file `index.html` after build project

```
<IfModule mod_rewrite.c>
     RewriteEngine On
     RewriteBase /
     RewriteRule ^index\.html$ - [L]
     RewriteCond %{REQUEST_FILENAME} !-f
     RewriteCond %{REQUEST_FILENAME} !-d
     RewriteRule . index.html [L]
</IfModule>
```

> Important in line `RewriteBase /`, if your html in root domain, you can use `/`, but if your html in sub-folder, ex: http://localhost/app then `RewriteBase /app/`

Open file `http.conf` in apache dir, change to:

```
<Directory "/var/www/html">
 AllowOverride All
</Directory>
```
restart apache service. try it! 

in windows slightly different configuration path, must to correct path.
