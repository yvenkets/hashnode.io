## Create Custom VPC IN AWS

## VPC - Virtual Private Cloud


> 
Amazon Virtual Private Cloud (Amazon VPC) enables you to launch AWS resources into a virtual network that you've defined. This virtual network closely resembles a traditional network that you'd operate in your own data center, with the benefits of using the scalable infrastructure of AWS.


- 
Amazon VPC is the networking layer for Amazon EC2.

### The following are the key concepts for VPCs:

**Virtual private cloud** (VPC) — A virtual network dedicated to your AWS account.

**Subnet **— A range of IP addresses in your VPC.

**Route table **— A set of rules, called routes, that are used to determine where network traffic is directed.

**Internet gateway** — A gateway that you attach to your VPC to enable communication between resources in your VPC and the internet.

**CIDR block** —Classless Inter-Domain Routing. An internet protocol address allocation and route aggregation methodology. 


## 1.Create VPC 


- 
So We will going to create VPC With the Below Network value **10.0.0.0/16**


- 
Open VPC Console on AWS.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629575160887/-Tu9uZ2Il.png)


- 
Config Screen

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629575528683/1n40_C1ca.png)


- 
When you create a VPC a Route Table, Network ACL, and Security Group are automatically created.

- 
Subnets or Internet Gateways are NOT automatically created, so we’ll create those below.

## 2.Create SubNets

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629614034145/nX7VbtAEP.png)


- 
We want to create the 2 subnets.


- 
1 subnet is public other 1 is private


- 
The below values i have assigned to my subnet.


> 
Public-Subnet  
Availability zone : ap-south-1a 
IPv4 CIDR block : 10.0.1.0/24

> 
Private-Subnet 
Availability zone : ap-south-1b
IPv4 CIDR block : 10.0.2.0/24


### Public Subnet

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629614367679/4scw_674i.png)

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629614414674/lQXsFCM4a.png)

### Private Subnet

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629614710068/SBm8qnwxf.png)

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629614736560/RChbivNKB.png)


- 
Now Our Subnet screen looks like.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629614801153/o7OaKxF73.png)

## 3.Create Internet gateway 


- 
Now we want to Create Internet gateway and attach it to custom VPC so that the VPC Will get the internet.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629615008922/aaTQGQgpfi.png)


- 
Give the Name for it.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629615063873/jgk7OBiLf.png)


- 
And attach to our newly created Custom VPC.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629615161224/sU093CJ4J.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629615201498/1qWEaU6fn.png)

## 4.Create new Route Table


- 
Now we want to create route table to route the traffic between subnets,internetgateway to public.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629615338890/-oUJFkPEI.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629615367694/e7d4hxUq7.png)


- 
Now we  need to give the Route Table (Custom Route) a route to the internet. 
Edit routes.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629615426917/LpjSXKYJ3.png)


- 
And add new route sourece is 0.0.0.0/0 to Newley created Internet gateway.



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629615560114/1B1ctbG5a.png)


- 
Lets associate a subnet we want to have internet access by going to the Subnet Associations and clicking on Edit.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629623527506/wVFd00IsU.png)


- 
I am onlyasocitae my public subnet


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629623583560/usajYkX4l.png)

- 
Now Our Public Subent have internet access and private subnet not having the internet access.


- 
After that we wanto modify the auto assign public ip settings to our public subnet.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629623738416/VkDuxGmc2.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629623766879/WOX0UW8uk.png)



- 
That's all Guys We have Successfully create one Full Functional Customized VPC.

## 5.Test The Custom VPC


- 
Now we will going to check our Custom VPC is working Properly or have any issue on the connectivity.

- 
For that We are going to launch Two EC2 Instance on that VPC.


- 
One instance in Public Subnet other one is private subnet.

**Public Subnet associated Instance**


- 
Here I Have selected Custom VPC and choose public subnet.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629628374535/2uhx9gufi.png)


- 
Then launch the instance with all the default values.

**Private Subnet associated Instance**


- 
Here i have selected Custom VPC and choose private subnet.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629628653087/d4NeoAItj.png)


- 
Then launch the instance with all the default values.


- 
Ok.Now we going to connect the instance via SSH.


> 
Here Two EC2 Instacnes are running one is public other one is private.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629628999673/YuC0XSC4M.png)


> 
See here there is no Public IP assigned for Private EC2 instance.

**Public Subnet Instance
**

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629629083374/bVun-RST9.png)


- 
Connect Private instance through Public Instance


- 
So i copied the .pem file to public instance.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629629337777/jBSoBKoBu.png)


- 
Now i am connected the public instance via ssh and then connect private instance from that.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629629543769/EEeV7cWsc.png)


- 
Yeah its connected and working perfectly.


> 
That's all guys... I have successfully created the Custom-VPC and configured and tested it.