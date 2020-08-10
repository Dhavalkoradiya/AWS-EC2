# AWS

EC2 is free for 12 month provided by Amazon Web Server(AWS). 
1. Host PHP + MySql Website
2. Domain and subdomain poining
3. Send mailer through SMTP with AWS SME

I am using windows.

## AWS Installation 

- Signup in AWS Console, you need to provide your Debit/credit card details.
- After completion of signup process, wait for 2 or 24 hours for activation your account.
1. After successfully signup. Select **Service** menu and choose **EC2** compute engine.
![ec2](https://image.prntscr.com/image/NDDJg6VLTUCACDnLJl22iw.png)

2. Click *Launch Instance* button.
3. Now Choose  Amazon Machine Image(AMI), it means Operating system. The best oprating system is Ubuntu(Linux) for PHP websites.
![ubuntu](https://image.prntscr.com/image/Q5IKYYHXT-iq9yR2SheJYQ.png)
I choose **Ubuntu Server 18.04**
4. After select button. you will click for *Review and Launch*.
After clicking Review and Launch You find the below screen, now click Launch button.
![Launch](https://image.prntscr.com/image/9buHoeq0QFOXD7H-PNS8lQ.png)
5. After Click *Launch* Button, You have to create a new key pair.
Goto -> Network & Security(sidepanel menu) -> Choose Key Pair.
![key-pair](https://image.prntscr.com/image/dBN3FxzLQb_ZXEN_riaLag.png)
6. Choose *create a new key pair* and give any relative name for key. Click to *Download Key Pair*. You will get an *.pem* file.
7. Now Instance has been created successfully. you can check status here.
![status](https://image.prntscr.com/image/tYMVkP-QRPaAbR39ddxoEg.png)

### Security Groups
Our application is web application so we need HTTP rule for that.
1. Goto -> Network & Security -> Choose *Security Groups*
2. If Already created Choose Rule and click *Edit inbound rule* Or click *Create security group*
![rule](https://image.prntscr.com/image/x3CTURYLRcuUTOmVKCUzkg.png)
3. Click *Add rule* and choose like below image.
![rule](https://image.prntscr.com/image/zA4MApWvRBqnL3YYt3hg4A.png)
After click on *save rule*.

This sercurity group must be associated with your instance.

### Elastic IP addresses
This step is very important in hosting things.
1. Goto -> Network & Security -> Choose *Elastic IPs* -> Choose *Allocate Elastic IP address*
![ip](https://image.prntscr.com/image/FzXXtX-OTXOIbjm7w8Cl-w.png)
2. Amazon will provide you a random IP address. associate IP address with instance box. see below image.
![ip](https://image.prntscr.com/image/Z6Kxj7UlTKyP6UyWpKFM6w.png)
3. Choose instance box here.
![ip](https://image.prntscr.com/image/t9MgbPqqQCy8QvLxEz7i4A.png)
4. Click *Associate* button. Elastic IP will added in your instance.

WooHoo! Your instance is ready to connect.

## Connecting to your Linux instance
1. Start PuTTY (from the Start menu, choose All Programs, PuTTY, PuTTY)
2. In the Category pane, choose Session and complete the following fields:
	- In the Host Name box, 
```bash	
	my-instance-user-name@my-instance-public-dns-name.
```
For Amazon Linux, the default user name is `ec2-user`. For RHEL5, the user name is often root but might be ec2-user. For Ubuntu, the user name is `ubuntu`. For SUSE Linux, the user name is `root`. For Debian, the user name is `admin`. Otherwise, check with your AMI provider.

- Ensure that the Port value is 22.
- Under Connection type, select SSH.

[Convert your *.pem* key to *.ppk* using PuTTYgen](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html#putty-private-key)

3. In the Category pane, expand Connection, expand SSH, and then choose Auth. Complete the following:
	- Choose Browse.
	- Select the `.ppk` file that you generated for your key pair and choose Open.
4. Choose Open.

Woohoo! you're connected to your instance.

## Windows connection

Run following command

```bash
ubuntu@ip-172-31-8-156:~$ sudo su
root@ip-172-31-8-156:/home/ubuntu#
```

This will update Ubuntu OS Packages
```bash
sudo apt-get update
```

Download XAMPP for 64 bit
```bash
wget https://www.apachefriends.org/xampp-files/7.4.8/xampp-linux-x64-7.4.8-0-installer.run
```

Make Execute Installation
```bash
sudo chmod +x xampp-linux-x64-7.4.8-0-installer.run
```

Run Installation
```bash
sudo ./xampp-linux-x64-7.4.8-0-installer.run
```

### XAMPP Installtion and Configration

```base
Select the components you want to install; clear the components you do not want to install. Click Next when you are ready to continue.

XAMPP Core Files : Y (Cannot be edited)

XAMPP Developer Files [Y/n] : Y

Is the selection above correct? [Y/n]: Y

Installation Directory

XAMPP will be installed to /opt/lampp

Press [Enter] to continue:

Do you want to continue? [Y/n]:Y
```

Run XAMPP
```bash
sudo /opt/lampp/lampp start
```

edit `httpd-xampp.conf`
```bash
vi /opt/lampp/etc/extra/httpd-xampp.conf
```
In this image there are default value is local you have to set `all granted`
![conf](https://image.prntscr.com/image/N9E_DaeRTAW_bM1BSNgltQ.png)

To save changes, press `escape`, and then type `:wq`, then hit enter. [VI Editor help](https://kb.iu.edu/d/adxz)

Restart XAMPP
```bash
sudo /opt/lampp/lampp restart
```

Security Settings
```bash
root@ip-172-31-8-156:/home/ubuntu# sudo /opt/lampp/xampp security
XAMPP:  Quick security check...
XAMPP:  MySQL is not accessable via network. Good.
XAMPP:  The MySQL/phpMyAdmin user pma has no password set!!!
XAMPP: Do you want to set a password? [yes] yes
XAMPP: Password:
XAMPP: Password (again):
XAMPP:  Setting new MySQL pma password.
XAMPP:  Setting phpMyAdmin`s pma password to the new one.
XAMPP:  MySQL has no root passwort set!!!
XAMPP: Do you want to set a password? [yes] yes
XAMPP:  Write the password somewhere down to make sure you won`t forget it!!!
XAMPP: Password:
XAMPP: Password (again):
XAMPP:  Setting new MySQL root password.
XAMPP:  Change phpMyAdmin`s authentication method.
XAMPP:  The FTP password for user `daemon` is still set to `xampp`.
XAMPP: Do you want to change the password? [yes] no
XAMPP:  Done.
root@ip-172-31-8-156:/home/ubuntu#
```

Thoes password keep be safe and used while connection and login in phpMyAdmin.

#### PhpMyAdmin
Access PhyMyAdmin at `http://IP-Address/phpmyadmin/`

#### Domain Settings
Assign domain to this instance.
If you own a domain address, go to domain DNS(Domain name settings). 
Add host value `@` points to `IP-Address`.
![domain](https://image.prntscr.com/image/F7Em-KPXQsGcSJPvtPVjFg.png)

#### FileZilla - File Uploads
Setup new site.

Open `New site`. Keep settings like below image and click `connect` button.

![filezilla](https://image.prntscr.com/image/R_4M81yTSYK_Q13jlyEoOw.png)

####  Domain Redirection using .htaccess
Create a *.htaccess* file and copy into `/opt/lampp/htdocs/` directory.
```bash
RewriteEngine On
RewriteCond %{HTTP_HOST} ^yourdomain.com
RewriteRule (.*) http://www.yourdomain.com/$1 [R=301,L]

RewriteCond %{HTTP_HOST} ^www\.yourdomain\.com$
RewriteCond %{REQUEST_URI} !^/WebsiteProjectFolder/
RewriteRule (.*) /WebsiteProjectFolder/$1
```

>  Now access your domain **http://YourDomain.com/**

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
