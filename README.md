# Multi-Domain CORS Support - Apache

## Basic Setup

1. You need to enable headers module to enable CORS in Apache. To do that, uncomment the following line:

```LoadModule headers_module modules/mod_headers.so```

2. Add the following header:

```Header add Access-Control-Allow-Origin "*”```

You can add this header to either your Apache config file, or .htaccess file, or Virtual Host configuration file, depending on your requirement. If you add it to your main configuration file, CORS will be enabled to all websites on your server. If you add it to .htaccess file or  virtual host configuration file, then it will be enabled for only that file’s website. The ```"*"``` here means all.

Examples:

```
Directory Tag in Main Configuration File
<Directory /var/www/html>
...
Header set Access-Control-Allow-Origin "*"
...
</Directory>
```

```
Anywhere in .htaccess file
...
Header add Access-Control-Allow-Origin "*"
...
```

```
VirtualHost Tag in Virtual Host Configuration File
<VirtualHost *:443>
...
Header add Access-Control-Allow-Origin "*"
...
</VirtualHost>
```

## Additional Optional Configurations

1. Enable CORS from one domain:

```
Header add Access-Control-Allow-Origin "example.com";
```

2. Enable CORS from multiple domains:

```
Header add Access-Control-Allow-Origin "example1.com";
Header add Access-Control-Allow-Origin "example2.com";
Header add Access-Control-Allow-Origin "example3.com";
```

3. Enable CORS from localhost:

```
Header add Access-Control-Allow-Origin "localhost";
```

4. To allow Access-Control-Allow-Origin (CORS) authorization for specific files only. For example to allow CORS for fonts only use following example:

```
<FilesMatch "\.(ttf|otf|eot|woff)$">
    <IfModule mod_headers.c>
        Header Set Access-Control-Allow-Origin "*"
    </IfModule>
</FilesMatch>
```