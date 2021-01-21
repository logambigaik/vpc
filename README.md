# Step1: Create VPC
![image](https://user-images.githubusercontent.com/58024415/95064316-3041d980-071d-11eb-999c-76ccfd7ddefb.png)

Click on Create VPC
# Step2: Create subnets
![image](https://user-images.githubusercontent.com/58024415/95064493-7008c100-071d-11eb-944d-5aa2cf838012.png)

Click on Create
# Create Internet Gateway
![image](https://user-images.githubusercontent.com/58024415/95064596-9595ca80-071d-11eb-94bd-1914c8226912.png)

Click on create internet gateway

Please attach VPC to our internet gateway
![image](https://user-images.githubusercontent.com/58024415/95064680-b65e2000-071d-11eb-88f8-559139af2c08.png)

Please select VPC and click on Attach Internet Gateway 
![image](https://user-images.githubusercontent.com/58024415/95064867-f2918080-071d-11eb-87e3-c20f864947b1.png)
# Create Route table
![image](https://user-images.githubusercontent.com/58024415/95064998-1654c680-071e-11eb-8166-1e5e51f1ce73.png)

Click on create

![image](https://user-images.githubusercontent.com/58024415/95065101-37b5b280-071e-11eb-9edf-d65cbfd742fd.png)

Goto Routes and click on Edit Routes

![image](https://user-images.githubusercontent.com/58024415/95065782-21f4bd00-071f-11eb-8847-0001dea53a7b.png)

Attach public subnet at Aubnet Associates

![image](https://user-images.githubusercontent.com/58024415/95065925-51a3c500-071f-11eb-9d9e-54d86184b4a0.png)

Click on save

![image](https://user-images.githubusercontent.com/58024415/95065244-63d13380-071e-11eb-8301-f07bebe8df5a.png)

Click on Add Route and provide 0.0.0.0/0 as Destination and internet gateway as Target

Now Create instance with this VPC and check whether you can able to connect or not

Please select VPC at configure system step

![image](https://user-images.githubusercontent.com/58024415/95065516-ca565180-071e-11eb-8da6-f2c9e46b8430.png)

Connect Instance using Mobaxterm or Putty

![image](https://user-images.githubusercontent.com/58024415/95066024-75ffa180-071f-11eb-9cee-a3c081b7130c.png)

# Create Private Subnet
![image](https://user-images.githubusercontent.com/58024415/95066491-1b1a7a00-0720-11eb-8ba8-6172499ff343.png)

Click on Create

Now Create instance with Private Subnet

![image](https://user-images.githubusercontent.com/58024415/95066662-5321bd00-0720-11eb-9a35-206246b1526a.png)

Selct Private Subnet and also keep Auto-assign Public IP as Disable and Click on Review & Launch. Select Key Pair and create instance

![image](https://user-images.githubusercontent.com/58024415/95067257-2f12ab80-0721-11eb-8673-1391bba99216.png)

See public ip not shown in below image. For connecting private server, we need server which is having public subnet vpc

copy keypair (.pem) file into public subnet server

![image](https://user-images.githubusercontent.com/58024415/95068532-0ab7ce80-0723-11eb-8218-ed50562613c7.png)

Change file permission using below command

    chmod 400 ekscluster.pem
    
Connect to private server using below command
    
    ssh -i ekscluster.pem ec2-user@10.0.2.216
![image](https://user-images.githubusercontent.com/58024415/95068755-4c487980-0723-11eb-8475-e27184529133.png)

But we may not access internet now, If we want internet we need to create NAT Gateway

![image](https://user-images.githubusercontent.com/58024415/95070177-5a979500-0725-11eb-8f32-96eb09426113.png)

Click on Create NAT Gateway

Goto Route Table and add select Route table when Main having "Yes"

![image](https://user-images.githubusercontent.com/58024415/95070582-f4f7d880-0725-11eb-8450-b4eb9025c0ec.png)

Click on Route and Click on Edit Route

![image](https://user-images.githubusercontent.com/58024415/95070645-0ccf5c80-0726-11eb-9e49-b68e5260d4ce.png)

Click on Save Routes

Now connect to sever and try to install JAVA once again

![image](https://user-images.githubusercontent.com/58024415/95070906-751e3e00-0726-11eb-89c2-bf3918795184.png)
