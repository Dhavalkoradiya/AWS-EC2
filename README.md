# AWS

EC2 is free for 12 month provided by Amazon Web Server(AWS). 
1. Host PHP + MySql Website
2. Domain and subdomain poining
3. Send mailer through SMTP with AWS SME

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
1. Goto -> Network & Security -> Choose Security Groups
2. If Already created Choose Rule and click *Edit inbound rule* Or click *Create security group*
![rule](https://image.prntscr.com/image/x3CTURYLRcuUTOmVKCUzkg.png)
3. Click *Add rule* and choose like below image.
![rule](https://image.prntscr.com/image/zA4MApWvRBqnL3YYt3hg4A.png)
After click on *save rule*.

This sercurity group must be associated with your instance.

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install foobar.

```bash
pip install foobar
```

```php
<?php

echo "hello";

?>
```

## Usage

```python
import foobar

foobar.pluralize('word') # returns 'words'
foobar.pluralize('goose') # returns 'geese'
foobar.singularize('phenomena') # returns 'phenomenon'
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
