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


open inbound connection through port 80:

Let's test how our Apache HTTP server can respond to requests from the Internet.
Open a web browser of your choice and try to access following url: http://<Public-IP-Address>:80
