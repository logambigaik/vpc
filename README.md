
# NAT Gateway image for VPC:  ( While creating NATGateway-subnet should be public but while in route , if main is Yes means thats associated with NAT so there we need to provide private subnet with NAT Route)
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

Please select VPC at configure system step(example-vpc)

![image](https://user-images.githubusercontent.com/54719289/108606838-997f6c00-73e2-11eb-9032-0ab119a0ab9b.png)

![image](https://user-images.githubusercontent.com/54719289/108606805-5f15cf00-73e2-11eb-8915-e39fd6102491.png)


Connect Instance using Mobaxterm or Putty

![image](https://user-images.githubusercontent.com/54719289/108606955-71dcd380-73e3-11eb-8978-166e8a5379ad.png)


# Creating instance after removing subnet under router table:
![image](https://user-images.githubusercontent.com/54719289/108607100-47d7e100-73e4-11eb-8d03-604e7c807a54.png)

# EC2 -Instance creation without subnet -Wont connect:

![image](https://user-images.githubusercontent.com/54719289/108607147-a43b0080-73e4-11eb-8b32-1e684bd3f695.png)




# Create Private Subnet:

![image](https://user-images.githubusercontent.com/54719289/108607562-1f9db180-73e7-11eb-9357-14c9fb73f06e.png)


Click on Create

![image](https://user-images.githubusercontent.com/54719289/108607577-347a4500-73e7-11eb-9dd1-ed5647fcee66.png)

# Create NAT Gateway Route:
    Specify any name, select public subnet and Allocate elastic IP
    
![image](https://user-images.githubusercontent.com/54719289/108609935-7b703680-73f7-11eb-8e82-4b02048d999d.png)

    For private, we need to select MAin as yes for example-vpc and     Update private subnet 
    
 ![image](https://user-images.githubusercontent.com/54719289/108608049-414c6800-73ea-11eb-9ba9-368e0cf9114a.png)


    Update Routes ( Choose NAT Gateway and enter ip as 0.0.0.0:
 
 ![image](https://user-images.githubusercontent.com/54719289/108608178-65f50f80-73eb-11eb-84f1-db074472abe1.png)
   
  

# Now Create instance with Private Subnet (before that update this subnet in route table):

    Selct Private Subnet and also keep Auto-assign Public IP as Disable and Click on Review & Launch. Select Key Pair and create instance

![image](https://user-images.githubusercontent.com/54719289/108607695-df8afe80-73e7-11eb-95f9-f7b3543abec4.png)

See public ip not shown in below image. For connecting private server, we need server which is having public subnet vpc

![image](https://user-images.githubusercontent.com/54719289/108607710-09442580-73e8-11eb-83ac-86c009bb73e8.png)


 Create .pem file in public (another EC2-instance)  , copy and paste the content of aws key pair file(KMGM in C:\G\KMGM.pem):
 
 ![image](https://user-images.githubusercontent.com/54719289/108608512-58408980-73ed-11eb-95fd-b19f70e219a4.png)

  
  Change file permission using below command

    chmod 400 test1.pem

 ![image](https://user-images.githubusercontent.com/54719289/108608564-bcfbe400-73ed-11eb-9c2d-f6d3ed1c04d1.png)

Connect to private server using below command
    
    ssh -i test1.pem ec2-user@10.0.2.87
   
 ![image](https://user-images.githubusercontent.com/54719289/108609140-fc2c3400-73f1-11eb-9080-354d14fe99aa.png)

    
# But we may not access internet now, If we want internet we need to create NAT Gateway

![image](https://user-images.githubusercontent.com/54719289/108609542-8ecdd280-73f4-11eb-887e-3862059c4f88.png)


        Click on Route and Click on Edit Route

        Goto Route Table and add select Route table when Main having "Yes"

![image](https://user-images.githubusercontent.com/54719289/108609588-e2d8b700-73f4-11eb-8e1d-371e671f3e9a.png)
![image](https://user-images.githubusercontent.com/54719289/108609605-00a61c00-73f5-11eb-8cfd-9a35a1175284.png)

        Also update the subnet
        
![image](https://user-images.githubusercontent.com/54719289/108609659-61355900-73f5-11eb-8ad4-f132651aaba3.png)



Now connect to sever and try to install git.

![image](https://user-images.githubusercontent.com/54719289/108610184-a0fe3f80-73f9-11eb-8cdf-f14bd8885ad5.png)

