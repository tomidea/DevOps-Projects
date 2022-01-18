# WEB STACK IMPLEMENTATION (LAMP STACK) IN AWS

Install Apache using Ubuntu’s package manager ‘apt’:
- update a list of packages in package manager:
  
  #sudo apt update
  
- run apache2 package installation:
  
  #sudo apt install apache2
  
 We used the below cmdlet to confirm that Nginx server is active

$ sudo systemctl status nginx

open inbound connection through port 80:

Let's test how our Apache HTTP server can respond to requests from the Internet.
Open a web browser of your choice and try to access following url: http://<Public-IP-Address>:80
