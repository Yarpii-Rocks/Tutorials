# Overview
If you have your Plesk 12.5 server configured to use nginx with PHP-FPM, you may require a configuration change in order to allow URL rewrites (" Permalinks " in WordPress) to display neat URL's. This is also required for other PHP platforms such as Magento.

With an Apache based system, this was normally set via the .htaccess file. However, nginx doesn't read this file so it must be added directly into the Plesk configuration.

# Instructions
1. Login to Plesk and select the domain you need to update.
1. Click on the "Apache and nginx settings" link:
![alt text](https://www.conetix.com.au/media/uploads/2015/10/29/plesk12_5-apache-and-nginx-settings_1.png)
1. Scroll right to the bottom and add the following to "Additional nginx directives":
```
if (!-e $request_filename){rewrite ^(.+)$ /index.php?q=$1 last;}
```
1. Click OK to save and apply.
1. You can now login to WordPress (or similar) to enable Permalinks.
