## Route 53 - Host our Domain name in Route 53 hosted zone.

# Route 53


- 
Amazon Route 53 is a highly available and scalable **cloud Domain Name System** (DNS) web service. It is designed to give developers and businesses an extremely reliable and cost effective way to route end users to Internet applications by translating names like www.example.com into the numeric IP addresses like 192.0.2.1 that computers use to connect to each other. Amazon Route 53 is fully compliant with IPv6 as well.


- 
Amazon Route 53 effectively connects user requests to infrastructure running in AWS – such as Amazon EC2 instances, Elastic Load Balancing load balancers, or Amazon S3 buckets – and can also be used to route users to infrastructure outside of AWS. 


- 
You can use Amazon Route 53 to configure DNS health checks, then continuously monitor your applications’ ability to recover from failures and control application recovery with Route 53 Application Recovery Controller.


### 1.Host our Domain name in Route 53 


- 
Here i a going to explain how to host our domain name in Route 53 that is already purchased in other DNS Registrar like Godaddy.


- 
I Have a domain name venketyuva.tk in Freenom.com


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629639015080/C4W3knGv4.png)


- 
To host this domain name in Route53 hosted zone we want to change the name server in Freenom console.


- 
For that we need to know AWS Route 53 service name servers records.


- 
So that i have going to first host my domain name in route 53.


- 
Open AWS Route 53 then create the hosted zone.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629639245642/-EWQAbRH0.png)


- 
Enter your domain name to be hosted here and create the hosted zone.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629639280809/Sz3O3U4R-.png)


- 
See here its shows AWS Name server records and SOA Records.
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629639337453/Sk-QieFmm.png)

### 2. Change the name server record in your previous DNS Registrar
- 
Copy the AWS Name server records and paste it in freenom custom name server filed.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629639462703/1PQ949KP9.png)


- 
To verify that check it in mxtoolbox website.

%[https://mxtoolbox.com › DNSLookup]




![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629640173075/klkiXsv4w.png)


> 
Its reflected in publicly.

### 3.Create Records In Route 53.


- 
To create the record in route 53 we will going to use our previos web server ip.


> 
In the below ip one websrver is running with my portfolio site.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629641475935/xpYBBX1ge.png)



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629641504175/bHOZNU6sh.png)

- 
We will going  to map the servers ip in route 53.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629641606904/ucYQle-pj.png)


- 
Here i have mapped with simple routing policy.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629641621177/TPobY6XiSW.png)

- 
Its working perfectly.
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629641644952/HK-HHQt5Y.png)




> 
There  is other one option to map server with your record thats cretae loadbalancer and put your ec2 instance behind that. Change the alias insted of ip values.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629642786089/fFRO4MNxp.png)

### 4.Route 53 also have some diffrent routing policy.


- 
Simple routing policy – Use for a single resource that performs a given function for your domain, for example, a web server that serves content for the example.com website.


- 
Failover routing policy – Use when you want to configure active-passive failover.


- 
Geolocation routing policy – Use when you want to route traffic based on the location of your users.


- 
Geoproximity routing policy – Use when you want to route traffic based on the location of your resources and, optionally, shift traffic from resources in one location to resources in another.


- 
Latency routing policy – Use when you have resources in multiple AWS Regions and you want to route traffic to the Region that provides the best latency with less round-trip time.


- 
Multivalue answer routing policy – Use when you want Route 53 to respond to DNS queries with up to eight healthy records selected at random.


- 
Weighted routing policy – Use to route traffic to multiple resources in proportions that you specify.

### 5.Test the Geolocation routing policy

Here i am going to create the same ip value but change the routing policy as geolocation.


> 
Geo location policy only working in specific geolocation only.


- 
I have created the geolocation policy for Africat continet only.
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629645617943/W2BWol039.png)


- 
So now the record only working for Africa continent only. currently i am in India.
we will check whether its working or not.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629645751437/MlgRgRrz2.png)

- 
Its not working in India.


- 
With the same IP we will create other record and let us check.

**DNS Record details**

> 
Record type = A

> 
Value = India.venketyuva.tk

> 
Points to = same IP


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629645829995/aHwBFdz6i.png)

- 
This working perfectly.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629646627220/FAekAgV8M.png)
**That's All guys we have learned the basics of Route53 and basic record creation.**