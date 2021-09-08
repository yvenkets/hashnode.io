## Amazon Certificate manager

AWS Certificate Manager is an Amazon Web Services tool that allows an IT team to provision, manage and deploy free Secure Sockets Layer (SSL) and Transport Security Layer (TSL) certifications in the AWS cloud.


- ACM is integrated with the following services:
Elastic Load Balancing
Amazon CloudFront – To use an ACM certificate with CloudFront, you must request or import the certificate in the US East (N. Virginia) region.
AWS Elastic Beanstalk
Amazon API Gateway
AWS CloudFormation


Types of Certificates For Use With ACM

Public certificates 

- 
ACM manages the renewal and deployment of public certificates used with ACM-integrated services.

- 
You cannot install public ACM certificates directly on your website or application, only for integrated services.
Private certificates

Private certificates

This is intranet certificate .so you can only use this with-in aws infra or hybrid cloud.

Imported certificates

You can import your own certificate that are already purchsed from other vendors.


Ok Now I am going to explain how to Create the certificate in AWS ACM.

Open AWS Certificate Manager in AWS Console.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630594705319/deOY1JNV2.png)
Select request public certificate option.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630594724648/2EEeyUyiP.png)
Now AWS Asking the domain name.enter your domain name.



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630597146023/gJcYWnLBC.png)
Now AWS ACM Validate our domain name to provide the certifate using two methods. one is dns validation and other one is email validation.

In DNS Validation we want to create records to verify the domain belongs to us.

In Email validation we want to send or receive the email to  confirm the domain belongs to us.

Here i am using DNS Validation method.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630597183541/LvOKuCBtD.png)
Next we want add tag for this resource.



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630597261303/_YoZYLVTO.png)
Finally we review and confirm the certificate request.

Finall step is validation ACM Validate our DNS Records.
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630597289039/e-QlmCxPC.png)

Its shows the pending validation.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630597341730/-CmrXJ-nd.png)



[image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630597404429/T83ff0a4z.png)


[image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630597432177/b1aTAbtm-.png)



[image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630597538099/qPjUA7m9q.png)

While configure ACM for DNS Validation it shows the option create record in Route53.

Route53 automatically create the essential record for you.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630597629780/UVZDp7Asy.png)



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630597648149/JUJ6EKOOg.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630597664115/ncCYBcqsf.png)


Its successfully create the record for you.
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630599473632/GYiP69upF.png)

Create Loadbalncer and attach the SSL certificate which ACM provided to our domain.

If you want to know much about how to configure classic load balancer check my previous article.


https://venket.hashnode.dev/configure-classic-load-balancer-in-aws

in the middle of load balancer configuration.
in the configure security settings select choose a certificate From ACM and choose which certificate from which one you want to configure for your website.
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630599577180/bXIIkthWi.png)

After successfully configure your load balancer your certificate merged with your loadbalancer.
so now we want to create the DNS A Record and map the load balancer name to it.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630599946896/GMy8WRbWI.png)

Now our website is secured with SSL. See the website with lock symbol.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630601235188/BVtEjoBF6.png)

in browser right click the lock symbol before the website name and again click the certificate link.
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630601281695/IwVWWog8K.png)

This Certificate issued by AWS ACM service
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630601329067/EdHjrEPJ8.png)

This Certificate is provided by amazon
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630601365027/3TQkTV3D_.png)
