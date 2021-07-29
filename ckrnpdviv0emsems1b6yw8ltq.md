## How To Host a static website in AWS S3 bucket and mapped to a custom domain with Godaddy

### S3 - What Is It?



- 
Amazon S3 is object storage built to store and retrieve any amount of data from anywhere. It’s a simple storage service that offers industry leading durability, availability, performance, security, and virtually unlimited scalability at very low costs.



- 
The S3 in Amazon S3 stands for Simple Storage Service. As the name implies it is a web service provided by Amazon Web Services which provides storage for the internet. This storage is highly-scalable and secure in the cloud. Having data stored in the cloud eliminates the need for in-house storage and customers can opt for unlimited storage or buy more as it is needed. 


- 
S3 is an incredibly helpful product which allows users to store and retrieve data from anywhere on the web, at any time. This is done though the AWS Management Console which is an easy to use web interface.


- 
Amazon itself uses S3 to run its own websites across the world. It has become extremely popular and is growing at an exponential rate.


- 
In 2007 S3 stored ten billion objects and this has soared to two trillion objects in 2013. Just a few of the well known companies that use S3 are Netflix, Dropbox, Pinterest and Tumblr.


**Web Hosting
**
There is two types of web hosting.

**Static web hosting 
**
its simple html pages dispaly our web content. only front end will display.

**Dynamic web hosting.
**
In dynamic webhosting code will be must compile with any server /service.

means Backend and front end must run.

## Host A Static Website in S3

### 1. Bucket creation and change the permissions.

Here i am going to explain how to host a static web content in S3.


- 
Open S3 Console in AWS.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627408291789/1w4oQq7Mu.png)


- 
Give a name and Create A bucket here.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627408417499/CDA7e49HX.png)



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627408477830/eAVIJM0Mo.png)


- 
Uncheck Public Access

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627408510530/dChIoL5ce.png)



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627408551594/TZeTF-L1Y.png)



- 
Create or select the content

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627408637287/lcRJonfyY.png)



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627408659772/99f6rdEwz.png)



- 
I am uploaded my the index.html file.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627408736968/wZr96Pi5U.png)

- 
Now  going to change the bucket properties.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627408755841/d7zPlnG0f.png)


- 
Enable statics website hosting and save changes.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627408789311/LvzMUAfYV.png)



- 
Next in the bucket permissions tab edit the bucket policy. add the below content to that.



```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::venketweb/*"
            ]
        }
    ]
}

``` 

and save changes.



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627408977719/TS_5jG5iI.png)



- 
Now going to bucket permission tab then going to static webhosting get the url.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627409073034/h0GLre36Kk.png)



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627409097107/Mja-mxGBq.png)


- 
Thats all we are hosted our static content in s3 bucket.

********************************************************************************


- 
For a change i will host my portfolio website in s3.

### 2. Content upload to S3

- 
Here i Just uploaded my contents.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627409606117/qvjCq6JBK.png)


- 
Wow its working perfectly with my contents.

## 3. Domain Mapping in Godaddy


- 
Now i am going to map custom domain for the s3 endpoint.


- 
Login to Godaddy and configure a Subdomain forward for s3 endpoint like below .



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627410183129/6npfNfiXC.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627410201199/WLvGDUHgP.png)



- 
This also working perfectly.

its

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627410041605/s7g8UftLe.png)

