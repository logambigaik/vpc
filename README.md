
# NAT Gateway image for VPC:
![image](https://user-images.githubusercontent.com/54719289/108605334-8caa4a80-73d9-11eb-8f25-0cb90c21af14.png)

# Subnet Mask - cheat sheet

![image](https://user-images.githubusercontent.com/54719289/108605535-98e2d780-73da-11eb-80da-89eb30d5afe6.png)

/16 ---> gives 65534 hosts and can create 65534 subnet 65534-ip address can create) 


# Step1: Create VPC

![image](https://user-images.githubusercontent.com/54719289/108605784-62a65780-73dc-11eb-853b-b5043e273c82.png)

Click on Create VPC
![image](https://user-images.githubusercontent.com/54719289/108605812-908b9c00-73dc-11eb-949c-8d6f8f5a378e.png)

# Step2: Create subnets

    Public subnet creation:

![image](https://user-images.githubusercontent.com/54719289/108606042-b8c7ca80-73dd-11eb-8801-15b6dcbe7a99.png)

Click on Create
![image](https://user-images.githubusercontent.com/54719289/108606056-d432d580-73dd-11eb-95e0-275ea3212e3f.png)

# Step3 Create Route table

![image](https://user-images.githubusercontent.com/54719289/108606149-63d88400-73de-11eb-9831-243b2f3f0b07.png)

    Click on create

![image](https://user-images.githubusercontent.com/54719289/108606175-8a96ba80-73de-11eb-9bcc-afbdd29cf42a.png)

# Create Internet Gateway

![image](https://user-images.githubusercontent.com/54719289/108606219-d21d4680-73de-11eb-9f26-69b5e974299a.png)

Click on create internet gateway

![image](https://user-images.githubusercontent.com/54719289/108606253-0f81d400-73df-11eb-85e4-3cb20bb26f32.png)

Please attach VPC to our internet gateway

![image](https://user-images.githubusercontent.com/54719289/108606310-769f8880-73df-11eb-9744-5d3838858881.png)

Please select VPC and click on Attach Internet Gateway 

![image](https://user-images.githubusercontent.com/54719289/108606324-8cad4900-73df-11eb-8d6c-44eb1770f83a.png)

![image](https://user-images.githubusercontent.com/54719289/108606394-df870080-73df-11eb-99ce-454dd3992cf0.png)

![image](https://user-images.githubusercontent.com/54719289/108606636-1b6e9580-73e1-11eb-84c8-910366015f99.png)


Goto Routes and click on Edit Routes (updated example-vpc route as example-route-vpc)

Click on Add Route and provide 0.0.0.0/0 as Destination and internet gateway as Target



![image](https://user-images.githubusercontent.com/54719289/108606478-47d5e200-73e0-11eb-9f61-ff7256a96828.png)

![image](https://user-images.githubusercontent.com/54719289/108606525-88cdf680-73e0-11eb-9f2d-6e967925d3f2.png)

Now, Attach public subnet under router table,

![image](https://user-images.githubusercontent.com/54719289/108606567-c894de00-73e0-11eb-9f89-7e961624e4db.png)

![image](https://user-images.githubusercontent.com/54719289/108606599-efebab00-73e0-11eb-8273-dfb28cafcf7d.png)

Click on save

![image](https://user-images.githubusercontent.com/54719289/108606652-2f19fc00-73e1-11eb-9aff-19a0767dec9f.png)



Now Create instance with this VPC and check whether you can able to connect or not

Please select VPC at configure system step



Connect Instance using Mobaxterm or Putty



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
