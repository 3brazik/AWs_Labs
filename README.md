# AWs_Labs
# AWS LAB

![MicrosoftTeams-image.png](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/MicrosoftTeams-image.png)

```markup
Steps
-Create Vpc 10.0.0.0/16
-create 2 subnets 1 public with 10.0.0.0/24 and private with 10.0.1.0/24 in AZ    
us-east-1a
-create 2 subnets public with 10.0.2.0/24 and private with 10.0.3.0/24 in AZ
us-east-1b
-create IGW and assign it to vpc 

```

![Screenshot from 2022-07-01 02-26-42.png](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Screenshot_from_2022-07-01_02-26-42.png)

```markup
-create  2 natgetway and attach each one to the public subnet 
-cretae 2 route tables for natgetway 
```

![Untitled](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Untitled.png)

![Screenshot from 2022-07-01 02-29-32.png](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Screenshot_from_2022-07-01_02-29-32.png)

```markup
-create ec2-public1 and assign it to  public subnet 1 and allow shh and http 
-cretae ec2-private1 and assign it to  private subnet 1 and allow shh and http --create ec2-public2 and assign it to  public subnet 2 and allow shh and http 
-cretae ec2-private1 and assign it to  private subnet 2 and allow shh and http 
```

```markup
in each ec2 write user data

#!/bin/bash
sudo yum update -y 
sudo yum install httpd -y 
sudo systemctl start httpd
sudo systemctl enable httpd 
```

![Untitled](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Untitled%201.png)

```markup
then create Target group for public instance and assign ec2-public 1 and 
ec2-public 2 to it
-create Target group for private instance and assign ec2-private 1 and ec2-private2 to it
```

![Screenshot from 2022-07-01 02-44-50.png](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Screenshot_from_2022-07-01_02-44-50.png)

![Untitled](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Untitled%202.png)

![Screenshot from 2022-07-01 02-45-08.png](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Screenshot_from_2022-07-01_02-45-08.png)

```markup
then create  public loadblancer 
-choose application loadblancer
-choose Internet-facing
-select two zones
-in Listeners and routing choose public target Group
-click create 
```

![Untitled](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Untitled%203.png)

![Untitled](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Untitled%204.png)

```markup
then create private loadblancer 
-choose application loadblancer
-choose Internal
-select two zones
-in Listeners and routing choose private target Group
-click create 
```

![Screenshot from 2022-07-01 02-55-18.png](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Screenshot_from_2022-07-01_02-55-18.png)

```markup
public load blancer 
```

![Screenshot from 2022-07-01 02-55-56.png](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Screenshot_from_2022-07-01_02-55-56.png)

```markup
private load blancer 
```

![Screenshot from 2022-07-01 02-58-04.png](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Screenshot_from_2022-07-01_02-58-04.png)

```markup
then 
go to the first public ec2 and ssh to it 
then write this command  
-sudo vim /etc/httpd/conf/httpd.conf
<VirtualHost *:*>
        ProxyPreserveHost on
        ServerAdmin ec2-user@localhost
        ProxyPass / http://enter the private dns name of the private load blancer/
        ProxyPassReverse / http://enter the private dns name of the private loadblancer/
</VirtualHost>
```

![Screenshot from 2022-07-01 03-08-53.png](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Screenshot_from_2022-07-01_03-08-53.png)

```markup
then 
-systemctl stop httpd
-systemctl start httpd
```

```markup
then do the same for ec2-public 2
```

![Untitled](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Untitled%205.png)

![Untitled](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Untitled%206.png)

![MicrosoftTeams-image.png](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/MicrosoftTeams-image.png)

```markup
Steps
-Create Vpc 10.0.0.0/16
-create 2 subnets 1 public with 10.0.0.0/24 and private with 10.0.1.0/24 in AZ    
us-east-1a
-create 2 subnets public with 10.0.2.0/24 and private with 10.0.3.0/24 in AZ
us-east-1b
-create IGW and assign it to vpc 

```

![Screenshot from 2022-07-01 02-26-42.png](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Screenshot_from_2022-07-01_02-26-42.png)

```markup
-create  2 natgetway and attach each one to the public subnet 
-cretae 2 route tables for natgetway 
```

![Untitled](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Untitled.png)

![Screenshot from 2022-07-01 02-29-32.png](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Screenshot_from_2022-07-01_02-29-32.png)

```markup
-create ec2-public1 and assign it to  public subnet 1 and allow shh and http 
-cretae ec2-private1 and assign it to  private subnet 1 and allow shh and http --create ec2-public2 and assign it to  public subnet 2 and allow shh and http 
-cretae ec2-private1 and assign it to  private subnet 2 and allow shh and http 
```

```markup
in each ec2 write user data

#!/bin/bash
sudo yum update -y 
sudo yum install httpd -y 
sudo systemctl start httpd
sudo systemctl enable httpd 
```

![Untitled](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Untitled%201.png)

```markup
then create Target group for public instance and assign ec2-public 1 and 
ec2-public 2 to it
-create Target group for private instance and assign ec2-private 1 and ec2-private2 to it
```

![Screenshot from 2022-07-01 02-44-50.png](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Screenshot_from_2022-07-01_02-44-50.png)

![Untitled](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Untitled%202.png)

![Screenshot from 2022-07-01 02-45-08.png](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Screenshot_from_2022-07-01_02-45-08.png)

```markup
then create  public loadblancer 
-choose application loadblancer
-choose Internet-facing
-select two zones
-in Listeners and routing choose public target Group
-click create 
```

![Untitled](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Untitled%203.png)

![Untitled](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Untitled%204.png)

```markup
then create private loadblancer 
-choose application loadblancer
-choose Internal
-select two zones
-in Listeners and routing choose private target Group
-click create 
```

![Screenshot from 2022-07-01 02-55-18.png](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Screenshot_from_2022-07-01_02-55-18.png)

```markup
public load blancer 
```

![Screenshot from 2022-07-01 02-55-56.png](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Screenshot_from_2022-07-01_02-55-56.png)

```markup
private load blancer 
```

![Screenshot from 2022-07-01 02-58-04.png](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Screenshot_from_2022-07-01_02-58-04.png)

```markup
then 
go to the first public ec2 and ssh to it 
then write this command  
-sudo vim /etc/httpd/conf/httpd.conf
<VirtualHost *:*>
        ProxyPreserveHost on
        ServerAdmin ec2-user@localhost
        ProxyPass / http://enter the private dns name of the private load blancer/
        ProxyPassReverse / http://enter the private dns name of the private loadblancer/
</VirtualHost>
```

![Screenshot from 2022-07-01 03-08-53.png](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Screenshot_from_2022-07-01_03-08-53.png)

```markup
then 
-systemctl stop httpd
-systemctl start httpd
```

```markup
then do the same for ec2-public 2
```

![Untitled](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Untitled%205.png)

![Untitled](AWS%20LAB%202c2c2f12014d4d469d47077b8e44e062/Untitled%206.png)




# AWS

![MicrosoftTeams-image (1).png](AWS%2063c60b3a73854e878621666a64bad131/MicrosoftTeams-image_(1).png)

```markup
Steps
-Create Vpc 10.0.0.0/16
-create 2 subnets 1 public with 10.0.0.0/24 and private with 10.0.1.0/24 in AZ    
us-east-1a
-create 2 subnets public with 10.0.2.0/24 and private with 10.0.3.0/24 in AZ
us-east-1b
-create IGW and assign it to vpc 
```

![Screenshot from 2022-07-01 02-26-42.png](AWS%2063c60b3a73854e878621666a64bad131/Screenshot_from_2022-07-01_02-26-42.png)

```markup
-create  2 natgetway and attach each one to the public subnet 
-cretae 2 route tables for natgetway 
```

![Untitled](AWS%2063c60b3a73854e878621666a64bad131/Untitled.png)

![Screenshot from 2022-07-01 02-29-32.png](AWS%2063c60b3a73854e878621666a64bad131/Screenshot_from_2022-07-01_02-29-32.png)

```markup
first create 2 Target Group  1 for Public subnets and 1 for private subnet 
if you have 2 created make sure you stop inctance inside it to use it in this 
lab 
```

![1.jpg](AWS%2063c60b3a73854e878621666a64bad131/1.jpg)

```markup
-we need to create 2 load blancer one for the public and one for the private to assign it to our AutoScallingg Group if you have one running already don't do this step 
-choose internet facing 

--in the private one choose internal 
--and select the private subnets 

```

![Untitled](AWS%2063c60b3a73854e878621666a64bad131/Untitled%201.png)

![Untitled](AWS%2063c60b3a73854e878621666a64bad131/Untitled%202.png)

```markup
in security group  make sure you allow http 
in listener make sure you chose you public target group 
then click create 
and do the same steps to create the private load blancer 
make sure you choose the private subnets and private Target group
```

![Untitled](AWS%2063c60b3a73854e878621666a64bad131/Untitled%203.png)

```markup
then go to Auto Scalling group 
1- select create launch template
```

![Untitled](AWS%2063c60b3a73854e878621666a64bad131/Untitled%204.png)

```markup
2 -start to configure your template
```

![Untitled](AWS%2063c60b3a73854e878621666a64bad131/Untitled%205.png)

```markup
ami-0cff7528ff583bf9a 
put this id and it will show directly to chooce amazon image
then choose t2 micro in instance type
```

![Untitled](AWS%2063c60b3a73854e878621666a64bad131/Untitled%206.png)

```markup

click advance network 
-the most important part in network 
make sure you enable auto assign public IPV4 to allow the instancee to connect 
the internet 
```

[https://www.notion.so](https://www.notion.so)

![Untitled](AWS%2063c60b3a73854e878621666a64bad131/Untitled%207.png)

```markup
then in user data 
write the following script 
#!/bin/bashsudo yum update -y
sudo yum install httpd -y
sudo systemctl enable --now httpd
sudo chmod 777 /etc/httpd/conf/httpd.conf
sudo echo -e "<VirtualHost *:*>\n\tProxyPreserveHost on\n\tServerAdmin ec2-user@localhost\n\tProxyPass / http://webservers-internal-loadbalancer-989703722.us-east-1.elb.amazonaws.com/\n\tProxyPassReverse / http://webservers-internal-loadbalancer-989703722.us-east-1.elb.amazonaws.com/\n</VirtualHost>">> /etc/httpd/conf/httpd.conf
sudo systemctl restart httpd

-make sure you replace the link with your private load blancer link 
then create the templete
```

![Untitled](AWS%2063c60b3a73854e878621666a64bad131/Untitled%208.png)

```markup
Go back to auto scalling and choose the templete
```

![Untitled](AWS%2063c60b3a73854e878621666a64bad131/Untitled%209.png)

```markup
and choose your vpc 
then select your first public subnet with 10.0.0.0/24
and the second subnet with 10.0.2.0/24
click next
```

![Untitled](AWS%2063c60b3a73854e878621666a64bad131/Untitled%2010.png)

![Untitled](AWS%2063c60b3a73854e878621666a64bad131/Untitled%2011.png)

![Untitled](AWS%2063c60b3a73854e878621666a64bad131/Untitled%2012.png)

```markup
then do the same for the private template
dont allow auto assgin public ipv4 in private templete  let it disable
but in user data 
write the following script 

#!/bin/bash
yum update -y
yum install -y httpd.x86_64
systemctl start httpd.service
systemctl enable httpd.service
echo “Hello World from $(hostname -f)” > /var/www/html/index.html

and create the auto scalling group for private instance 
then use the public load blancer url and it will be work Insha Allah 
```


# AWS Lab

# Mohamed AbdelRazek

![MicrosoftTeams-image (2).png](AWS%20Lab%205799c83795c9484f96d2b0f64839e21a/MicrosoftTeams-image_(2).png)

```markup

```

![Untitled](AWS%20Lab%205799c83795c9484f96d2b0f64839e21a/Untitled.png)

![Untitled](AWS%20Lab%205799c83795c9484f96d2b0f64839e21a/Untitled%201.png)

just test

![Untitled](AWS%20Lab%205799c83795c9484f96d2b0f64839e21a/Untitled%202.png)

create load balancer service 

![Untitled](AWS%20Lab%205799c83795c9484f96d2b0f64839e21a/Untitled%203.png)

```markup
then modifying it to print my ip 
create docker file 

and pushing it to ECR
```

![Untitled](AWS%20Lab%205799c83795c9484f96d2b0f64839e21a/Untitled%204.png)

![Untitled](AWS%20Lab%205799c83795c9484f96d2b0f64839e21a/Untitled%205.png)

then adding the image to deployment

![Untitled](AWS%20Lab%205799c83795c9484f96d2b0f64839e21a/Untitled%206.png)

![Untitled](AWS%20Lab%205799c83795c9484f96d2b0f64839e21a/Untitled%207.png)

after getting loadbalancer url 

![Untitled](AWS%20Lab%205799c83795c9484f96d2b0f64839e21a/Untitled%208.png)

![Untitled](AWS%20Lab%205799c83795c9484f96d2b0f64839e21a/Untitled.png)