
1. In your browsers go to http://localhost or http://127.0.0.1, you should receive no response (no response header). If you receive any response this means you may have Apache, IIS or other software that is serving your local 80 ports. So firstly uninstall or stop the corresponding services or software.
2. Go to https://www.apachelounge.com/download, download and install  vc_redist_x64
3. In your hard drive consider a whole partition or a top level folder to store all of your development related files and folders. We refer to this location as *workshop* and in this tutorial we use drive `d:` as our workshop location. In workshop, create three folders: 
    * `www` storing your codebases, for each project create a folder in this folder
    * `data` contains all your databases and other storage. 
    * `server` contains all server tools required to make you site running, apache, mysql, php, ...
    
 4. Download `Apache 2.4.* Win64` file from  https://www.apachelounge.com/download and extract its content somewhere in you computer. In its extracted folder rename `Apache24` folder to `httpd` and move it to `D:\server\`.
    5. Download `php-7.x.x-Win32-VC15-x64.zip` from http://windows.php.net/download/ and extract its content to `D:\server\php` 
    6.  Download `mysql-5.7.x-winx64.zip` from https://dev.mysql.com/downloads/mysql/ or other sites if access is forbidden. and extract its content to `D:/server/mysql`
    7. Download *PathEditor* utility from https://patheditor2.codeplex.com/ and run it.
    8. Using PathEditor add the following paths to your system path. 
       - `D:\server\php`
       - `D:\server\mysql\bin`
       - `D:\server\httpd\bin` 
    9. Create a folder named confg in `D:\server` to store all of our apache configuration files.
    10. Create `_php.conf` file in `D:\server\conf` folder to register php handler to Apache HTTP server. With the following content
    
     LoadModule php7_module  "D:\server\php\php7apache2_4.dll"
     PHPIniDir "D:/server/php"
    
    <IfModule mime_module>
        AddType application/x-httpd-php .phtml
        AddType application/x-httpd-php .php
    </IfModule>

   12.  Add `Include D:/server/conf/*.conf` to the end of `D:/httpd/conf/httpd.conf`, append a `#` to the beginning of `ServerRoot "c:/Apache24"` at line 37 and `DocumentRoot "c:/Apache24/htdocs"` at line 246
to comment them out and finally save the file. 
   13.  Open cmd and run `httpd -t`, you should see `Syntax OK` message. 
   14.  Open cmd ad administrator and run `httpd -k install` and `httpd -k start` to install and start apache http server. 
   15. Now if you go to `http://localhost` you should receive some sort of response. (`Forbidden
You don't have permission to access / on this server.` message.)
  16. (optional) Download  from https://www.apachelounge.com/download/ and extract `mod_xsendfile.so` to `D:\server\httpd\modules`
4. Download `php_xdebug-*.dll` file from https://xdebug.org/download.php and rename it to php_xdebug.dll and move it to `D:\server\php\ext`

Intl Extension
-----------------
1. uncomment `extension=php_intl.dll` in php.ini
2. Copy all `icu*.dll` files from php home to apache's `bin` folder.
3. Restart apache.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0MjQwMzAyMjBdfQ==
-->