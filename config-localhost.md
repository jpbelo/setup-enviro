## config localhost with .test TLD, keys for gitlab and github


1. new folder ``Sites`` on the user root level - ``mkdir ~/Sites``


1. setup Fork for Gitlab

   1. on Fork, Gitlab section - log in...
   2. on gitlab.com, settings -> access tokens - create a personal access token
   3. paste the access token on fork
   4. on terminal, ``ssh-keygen -t rsa -C "your.email@example.com" -b 4096`` to generate a SSH key
   5. ``pbcopy < ~/.ssh/id_rsa.pub`` to put the key in the clipboard (if using Fork, there's no need to copy, next step will make it unnecessary)
   6. on Fork, gitlab section, SSH keys tab, Add SSH keys (it should have already selected the public key)

2. on Fork, clone gitlab repos into the ``Sites`` folder

4. install Homebrew - ``ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`` ( use ``brew up`` to update)

5. install dnsmasq - ``brew install dnsmasq``

6. create user conf

   1. ``cd /etc/apache2/users``

   2. ``sudo nano username.conf`` - replace all mentions of ``username`` with your computer short name 

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
      2. or, in case you are on High Sierra or latter, ``LoadModule php7_module libexec/apache2/libphp7.so``
   3. also uncomment this configuration file:
      1. ``Include /private/etc/apache2/extra/httpd-userdir.conf``

8. edit httpd-userdir.conf - ``sudo nano /etc/apache2/extra/httpd-userdir.conf``

   1. uncomment this: ``Include /private/etc/apache2/users/*.conf``

9. restart apache - ``sudo apachectl restart``

10. ``localhost/~username`` should now show the contents of sites folder

11. allow any **.htaccess** files used to override the default settings - change **AllowOverride None** to **AllowOverride All** - ``sudo nano /etc/apache2/httpd.conf`` - around line 258

    1. ​

    ```
    #
    # Possible values for the Options directive are "None", "All",
    # or any combination of:
    #   Indexes Includes FollowSymLinks SymLinksifOwnerMatch ExecCGI MultiViews
    #
    # Note that "MultiViews" must be named *explicitly* --- "Options All"
    # doesn't give it to you.
    #
    # The Options directive is both complicated and important.  Please see
    # http://httpd.apache.org/docs/2.4/mod/core.html#options
    # for more information.
    #
    Options FollowSymLinks Multiviews
    MultiviewsMatch Any

    #
    # AllowOverride controls what directives may be placed in .htaccess files.
    # It can be "All", "None", or any combination of the keywords:
    #   AllowOverride FileInfo AuthConfig Limit
    #
    AllowOverride None

    #
    # Controls who can get stuff from this server.
    #
    Require all granted
    ```

    ​









``sudo mkdir /etc/resolver``

``sudo nano /etc/resolver/test``

add ``nameserver 127.0.0.1``





``sudo nano /usr/local/etc/dnsmasq.conf``

at the end paste ``address=/.test/127.0.0.1``



start dnsmasq automatically

``sudo brew services stop dnsmasq``

``sudo brew services start dnsmasq``



Test - ``dig foo.test @127.0.0.1 ``  ou  ``ping foo.test``







Now to make Apache handle any request from a .test TLD and match it to the corresponding directory in the Sites dir. 



edit ``httpd.conf`` - ``sudo nano /etc/apache2/httpd.conf`` - to uncomment the vhosts and the alias

```
# Virtual hosts
Include /private/etc/apache2/extra/httpd-vhosts.conf

...

LoadModule vhost_alias_module ...
```

comment

```
220 <Directory />
221     AllowOverride none
222     Require all denied
223 </Directory>
```









edit the ``vhosts`` - ``sudo nano /etc/apache2/extra/httpd-vhosts.conf`` - add this and change username with your username

```
<Directory "/Users/username/Sites/">
  AllowOverride All
  Options Indexes MultiViews FollowSymLinks
  Require all granted
</Directory>

<VirtualHost *:80>
  ServerName local.test
  ServerAlias *.test
  UseCanonicalName off
  VirtualDocumentRoot /Users/username/Sites/%1/
</VirtualHost>
```



``sudo apachectl restart``









update homebrew and install node (npm is inside)
```
brew update
brew install node
```

make sure it's installed - check versions
```
node -v
npm -v
```

install grunt command line interface globally
```
npm install -g grunt-cli
```



```
npm -g list --depth=0

├── browserify@14.5.0
├── create-react-app@1.5.2
├── create-react-native-app@1.0.0
├── exp@47.4.4
├── grunt-cli@1.2.0
├── npm@5.8.0
├── react-devtools@3.2.1
├── react-native-cli@2.0.1
├── react-native-git-upgrade@0.2.7
├── rollup@0.51.8
├── stylus@0.54.5
└── yarn@1.6.0
```





## Sources:

https://coolestguidesontheplanet.com/get-apache-mysql-php-and-phpmyadmin-working-on-macos-sierra/

http://harold.internal.org/using-dnsmasq-on-osx-sierra-for-local-dev-domain-wildcards/

http://alexking.org/blog/2015/04/20/dev-app-dnsmasq

permissions

https://stackoverflow.com/questions/38037448/apache-config-virtualdocumentroot




## Notes:
```
sudo apachectl start
sudo apachectl stop
sudo apachectl restart
httpd -v
```



