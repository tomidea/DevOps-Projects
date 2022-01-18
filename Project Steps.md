# WEB STACK IMPLEMENTATION (LAMP STACK) IN AWS

Install Apache using Ubuntu’s package manager ‘apt’:
- update a list of packages in package manager:
  
  *#sudo apt update*
  <img width="866" alt="Sudo apt update" src="https://user-images.githubusercontent.com/51254648/149948586-f8fb8dcc-4555-4d3f-9c8d-d80827fa8fd6.png">

  
- run apache2 package installation:
  
  *#sudo apt install apache2*
  <img width="1280" alt="Install apache2" src="https://user-images.githubusercontent.com/51254648/149949310-b992f369-e0fa-4dd2-93fc-b1fecf6432dc.png">
  
 We used the below cmdlet to confirm that Nginx server is active

*$ sudo systemctl status nginx*

<img width="651" alt="Apache running active" src="https://user-images.githubusercontent.com/51254648/149950174-78930ed3-cebf-42b5-8dca-1f50d0ffe80e.png">

Edit the inbound rule to open inbound connection through port 80:

<img width="1219" alt="open inbound connection port 80" src="https://user-images.githubusercontent.com/51254648/149950744-2e7d2016-1315-41da-89ce-94b154bb65c7.png">

let us try to check how we can access it locally in our Ubuntu shell, run:
curl http://localhost:80

<img width="907" alt="Access apache2 on shell" src="https://user-images.githubusercontent.com/51254648/149950820-fe159464-d7b4-4fdf-9c94-ab46dee738d3.png">

or
 curl http://127.0.0.1:80
 <img width="993" alt="access apache2 on shell 2" src="https://user-images.githubusercontent.com/51254648/149950841-7fbaf4cb-54d9-4820-8b3f-da41c5061496.png">

 
Let's test how our Apache HTTP server can respond to requests from the Internet.
Open a web browser of your choice and try to access following url: 

*http://<Public-IP-Address>:80*
 <img width="1278" alt="Apache2 default page" src="https://user-images.githubusercontent.com/51254648/149950847-6f7930b5-340f-4c10-b570-69205a633c54.png">

 ## STEP 2 — INSTALLING MYSQL
  
  Again, use ‘apt’ to acquire and install this software:

*sudo apt install mysql-server*
  <img width="1275" alt="Install My-sql" src="https://user-images.githubusercontent.com/51254648/149956124-8cf828c0-aeac-492c-ae6b-59e5922b905b.png">
  
  This script will remove some insecure default settings and lock down access to your database system. Start the interactive script by running:
*sudo mysql_secure_installation*
 
  <img width="720" alt="mysql secure installation" src="https://user-images.githubusercontent.com/51254648/149956149-002608d0-a56f-48b0-8746-3d78613f0126.png">
 
  Access MySQL console by typing: *sudo mysql*

  <img width="568" alt="access mysql" src="https://user-images.githubusercontent.com/51254648/149956155-c4b18315-a15b-4e85-9e36-f97d88fe549a.png">

  
  ## STEP 3 — INSTALLING PHP
  We need libapache2-mod-php to enable Apache to handle PHP files. Core PHP packages will automatically be installed as dependencies. To install these 3 packages at once, run:

*sudo apt install php libapache2-mod-php php-mysql*
   <img width="1074" alt="install 3 core packages" src="https://user-images.githubusercontent.com/51254648/149958291-179e8c39-5ba2-479c-8963-ed96f41224be.png">

After installation, Check the version using this command:
  *php -v*

  <img width="485" alt="PHP version" src="https://user-images.githubusercontent.com/51254648/149958307-f75fe5d1-2bc7-4417-9b58-ea3568eea2ce.png">
  

  ## STEP 4 — CREATING A VIRTUAL HOST FOR YOUR WEBSITE USING APACHE
  Apache on Ubuntu 20.04 has one server block enabled by default that is configured to serve documents from the /var/www/html directory.
  We will leave this configuration as is and will add our own directory next next to the default one.

Create the directory for projectlamp using ‘mkdir’ command as follows:
  *sudo mkdir /var/www/projectlamp*
 
 Next, assign ownership of the directory with your current system user:

 *sudo chown -R $USER:$USER /var/www/projectlamp*

 Create and open a new configuration file in Apache’s sites-available directory using your preferred command-line editor.
  *sudo vi /etc/apache2/sites-available/projectlamp.conf*
  
  Paste in the following bare-bones configuration by hitting on i on the keyboard to enter the insert mode, and paste the text:
  
  <VirtualHost *:80>
    ServerName projectlamp
    ServerAlias www.projectlamp 
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/projectlamp
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
  
  <img width="375" alt="Barebone text" src="https://user-images.githubusercontent.com/51254648/149966439-e50de19e-2c98-4bc8-b5fd-d68d01baf745.png"> 
 
  Use the ls command to show the new file in the sites-available directory

*sudo ls /etc/apache2/sites-available*
  
  <img width="453" alt="Show new file" src="https://user-images.githubusercontent.com/51254648/149967344-7a7d739f-5163-40f9-b9e4-12aca8dae6e2.png">
  
 To disable Apache’s default website use a2dissite command , type: *sudo a2dissite 000-default*
 To make sure your configuration file doesn’t contain syntax errors, run: *sudo apache2ctl configtest*
 Reload Apache so these changes take effect: *sudo systemctl reload apache2*
  <img width="1278" alt="enable new virtual host" src="https://user-images.githubusercontent.com/51254648/149966461-3d26f7ca-2d03-41c8-95a4-bfd23234a41c.png">

 Now go to your browser and try to open your website URL using IP address: *http://52.91.92.61:80*
  <img width="1279" alt="Access apache virtual host on browser" src="https://user-images.githubusercontent.com/51254648/149966455-7974e38d-8474-4793-a42a-15cf5bf638de.png">
 
  
 ## STEP 5 — ENABLE PHP ON THE WEBSITE
  With the default DirectoryIndex settings on Apache, a file named index.html will always take precedence over an index.php file. To change this behavior, we need to edit the /etc/apache2/mods-enabled/dir.conf file and change the order in which the index.php file is listed within the DirectoryIndex directive:
  
  *sudo vim /etc/apache2/mods-enabled/dir.conf*
  <IfModule mod_dir.c>
        #Change this:
        #DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
        #To this:
        DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>
  
  Save and reload Apache server: *sudo systemctl reload apache2*
  
  Create a new file named index.php inside your custom web root folder:
    *vim /var/www/projectlamp/index.php*
  
  Add the following text, which is valid PHP code, inside the file:
<?php
phpinfo();

When you are finished, save and close the file, refresh the page and you will see a page similar to this:

  
After checking the relevant information about our PHP server through that page, it’s best to remove the file we created as it contains sensitive information about your PHP environment -and our Ubuntu server. You can use rm to do so:

*sudo rm /var/www/projectlamp/index.php*

