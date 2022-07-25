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
