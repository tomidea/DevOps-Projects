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
