# website-deployment-with-vagrant

running the included vagrant file should deploy and make the HTML website template in this link browsable https://www.tooplate.com/zip-templates/2133_moso_interior.zip ![image](https://github.com/envyvalery/website-deployment-with-vagrant/assets/140969141/729ca103-d765-4802-9269-6230ab699ded)

vagrant file to automate website deployment on VMS using Vagrant and Oracle virtual box.
We will use vs code and deploy the vagrant file as infra as code 

	• Open and Edit the vagrant file in vs code 
	- Private IP
	- Enable virtual box provider 
	- Edit RAM size 
	- The section for shell script for dependencies installation. This is same as user data in cloud computing eg installing httpd, running systemctl start httpd, systemctl enable httpd, mkdir -p /tmp/moso (this is to create a directory for where we will download our html template -p is to avoid interuptios even if the folder exists otherwise -p is not necesary, cd /tmp/moso, wget the-html-link , unzip -o the-html-file-name (-o is just to overide if the file already exists), cp -r th-html-file-name/* /var/www/html, systemctl restart httpd, cd /tmp/, rm -rf /temp/moso. When automating make sure to use -y..to prevent popups,
example
user data
   yum install httpd wget unzip vim -y
     apt-get install -y apache2
     systemctl start httpd
     systemctl enable httpd
     mkdir -p /tmp/moso
     cd /tmp/moso
     wget https://www.tooplate.com/zip-templates/2133_moso_interior.zip
     unzip -o 2133_moso_interior.zip
     cp -r 2133_moso_interior/* /var/www/html
     systemctl restart httpd
     cd /tmp/
     rm -rf /temp/moso

Note that these are all the same steps  followed in the manual process, but in this case, we are including everything in our bash script to run in the order provided to deploy the website  ! [image](https://github.com/envyvalery/website-deployment-with-vagrant/assets/140969141/a88949ac-3892-49ee-8806-9689eb84a302)
