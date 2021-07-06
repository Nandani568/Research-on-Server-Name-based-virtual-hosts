# Research-on-Server-Name-based-virtual-hosts
Research on Server, Name based virtual hosts


Creating a Name based Virtual Host[using Apache Server]

Step 1: Prerequisites (If Apache is not installed then install it with the below commands)

  sudo apt-get update -y
  
  sudo apt-get install apache2 -y
  
we will be creating the virtual host for domains:

Test1.com

Test2.com


Step 2: Create a Directory Structure. 

In this step we have to create directories for our different websites that we want to host on the server.

sudo mkdir -p /var/www/test1.com/public_html

sudo mkdir -p /var/www/test2.com/public_html

Step 3: Permissions

sudo chown -R $USER:$YOUR_USER_NAME /var/www/test1.com/public_html

sudo chown -R $USER:$ YOUR_USER_NAME /var/www/test2.com /public_html


Step 4: Create Sample (Demo) Pages for Each of the Virtual Hosts. 

In this step we are creating some sample pages for our two different websites. They are test1.com and test2.com.

vim /var/www/test1.com/public_html/index.html

<html>
  
<head>

  <title>Home Page of Saaspect Test1.com</title>

  </head>

  <body>

    <p>Success! The Saaspect test1 virtual host is working!</p>

  </body>

</html>
************************************************************

vim /var/www/test2.com/public_html/index.html
 
<html>

  <head>

    <title>Home Page of Saaspect Test2.com</title>

  </head>

  <body>

    <p>Success! The Saaspect test2 virtual host is working!</p>

  </body>
  
</html>

 
Step 5: To create the New Files for Virtual Host

In this step we have to create configuration files for both our websites. As we have already installed the Apache so we will be having the default configuration file, we will be 

using that and modifying that to create new configuration files for our websites.
  
sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/test1.conf
  
  ****It will look like this
<VirtualHost *:80>
ServerAdmin webmaster@localhost
DocumentRoot /var/www/html
ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
***For Test1.config

ServerAdmin admin@test1.com

ServerName test1.com

ServerAlias www.test1.com

DocumentRoot /var/www/test1.com/public_html.
 
**For Test2.config

ServerAdmin admin@test2.com

ServerName test1.com

ServerAlias www.test2.com

DocumentRoot /var/www/test2.com/public_html
  
Step 6: Configuring local DNS

In this step we are configuring the local DNS so that the domain points to the localhost
  
ip a
  
Vi /etc/hosts

Ip address test1.com

Ip address test2.com
  
Step 7: To Enable Files of Virtual Host

We have newly configured the virtual files or the configuration files for our websites so we need to explicitly enable them using the below commands.
  
sudo a2ensite test1.conf
  
sudo a2ensite test2.conf

Step 8: Restart Apache2
 
Once it is done then we need to restart our apache server. Then we are good to go.
  
sudo service apache2 restart

Output:

Go to Browser 

hit your ip address[get your default page]

write test1.com[get your index.html]

write test2.com[get your index.html]



