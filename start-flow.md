1. new folder localhost on the Desktop

1. setup Fork for Gitlab
   1. on Fork, Gitlab section - log in...
   2. on gitlab.com, settings -> access tokens - create a personal access token
   3. paste the access token on fork
   4. on terminal, ssh-keygen -t rsa -C "your.email@example.com" -b 4096 to generate a SSH key
   5. pbcopy < ~/.ssh/id_rsa.pub to put the key in the clipboard (if using Fork, there's no need to copy, next step will make it unnecessary)
   6. on Fork, gitlab section, SSH keys tab, Add SSH keys (it should have already selected the public key)
2. on Fork, clone gitlab repos into the localhost folder1. new folder ``Sites`` on the user root level


1. setup Fork for Gitlab

   1. on Fork, Gitlab section - log in...
   2. on gitlab.com, settings -> access tokens - create a personal access token
   3. paste the access token on fork
   4. on terminal, ``ssh-keygen -t rsa -C "your.email@example.com" -b 4096`` to generate a SSH key
   5. ``pbcopy < ~/.ssh/id_rsa.pub`` to put the key in the clipboard (if using Fork, there's no need to copy, next step will make it unnecessary)
   6. on Fork, gitlab section, SSH keys tab, Add SSH keys (it should have already selected the public key)

2. on Fork, clone gitlab repos into the ``localhost`` folder

3. open codekit, and setup the settings for the new projects ( File > Edit Defaults For New Projects - cmd + D )

   1. Project settings
      1. browser refreshing - external server options, turn switch ``on`` and ``http://localhost `` in the address field
      2. build process, enable ``on``
   2. languages
      1. javascript
         1. ESLint
         2. minify output with UglifyJS ``off``
      2. CSS
         1. style ``compact``

4. install Homebrew - ``ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`` ( use ``brew up`` to update)

5. install dnsmasq - ``brew install dnsmasq``

6. create user conf

   1. ``cd /etc/apache2/users``

   2. ``sudo nano username.conf`` - replace username with your computer short name 

   3. ```
      <Directory "/Users/username/Sites/">
      AllowOverride All
      Options Indexes MultiViews FollowSymLinks
      Require all granted
      </Directory>
      ```

   4. change permissions - ``sudo chmod 644 username.conf``

7. edit http.conf - ``sudo nano /etc/apache2/httpd.conf``

   1. make sure these modules are uncommented (the first 2 should already be on a clean install):
      1. ``LoadModule authz_core_module libexec/apache2/mod_authz_core.so``
      2. ``LoadModule authz_host_module libexec/apache2/mod_authz_host.so``
      3. ``LoadModule userdir_module libexec/apache2/mod_userdir.so``
      4. ``LoadModule include_module libexec/apache2/mod_include.so``
      5. ``LoadModule rewrite_module libexec/apache2/mod_rewrite.so``
   2. also to get php running uncomment
      1. ``LoadModule php5_module libexec/apache2/libphp5.so``
      2. or, in my case ``LoadModule php7_module libexec/apache2/libphp7.so``
   3. also uncomment this configuration file:
      1. ``Include /private/etc/apache2/extra/httpd-userdir.conf``

8. edit httpd-userdir.conf - ``sudo nano /etc/apache2/extra/httpd-userdir.conf``

   1. uncomment this: ``Include /private/etc/apache2/users/*.conf``

9. restart apache - ``sudo apachectl restart``

10. ``localhost/~username`` should now show the contents of sites folder





https://coolestguidesontheplanet.com/get-apache-mysql-php-and-phpmyadmin-working-on-macos-sierra/







```
sudo apachectl start
sudo apachectl stop
sudo apachectl restart
httpd -v
```









3. open codekit, and setup the settings for the new projects ( File > Edit Defaults For New Projects - cmd + D )
   1. Project settings
      1. browser refreshing - external server options, turn switch on and http://localhost in the address field
      2. build process, enable on
   2. languages
      1. javascript
         1. ESLint
         2. minify output with UglifyJS off
      2. CSS
         1. style compact




