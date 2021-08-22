## Change EC2 Instance Type Using Lambda Function

### AWS Lambda
              
> 
AWS Lambda is a serverless compute service that lets you run code without provisioning or managing servers, creating workload-aware cluster scaling logic, maintaining event integrations, or managing runtimes.


**AWS Cost Saving
**
In the Cloud infrastructure all the clients need to cut the cost on infrastructure's that this article helps you to cut the cost on AWS Server infra.


- 
Here I Am Going to explain how to automate the AWS EC2 instance type at the scheduled times.

### 1.Create Policy


- 
First we want to create the Policy to allow some attributes for EC2.

**IAM Console -> Policy -> Create Policy ->Select Json Tab -> clear all an paste the above content.**


```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:StartInstances",
                "ec2:Stopinstances",
                "ec2:DescribeInstances",
                "ec2:CopySnapshot",
                "ec2:Describe*",
                "ec2:CreateTags",
                "ec2:*",
                "ec2:CreateSnapshot"
            ],
            "Resource": "*"
        }
    ]
}
``` 




![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629568854633/4n8wMURzF.png)




![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629568891581/ZG-nTQ0TX.png)

Finally create the policy.


### 2.Create Role


- 
Then we want to create the Role For Modify the instance type.


- 
In the IAM Console Create Role.


- 
Select the Lambda as use case and next.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629569444218/CZvOvFhyp.png)


- 
Then attached the policy you created in previous step.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629569566364/ZYKyBDFSXz.png)


- 
Then Give name and create.



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629569648260/LbKj4gxL_.png)

### 3.Create Lambda Function.


- 
In the Lambda Console create a function -> "Author from scratch" -> Select function name as Modify instance -> select Nodejs ==> Use an existing role ==> select our prvious created role 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629570643416/5kT12iGmXp.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629570692122/jETQLBYj2.png)


- 
Configure The Lambda Function Code


- 
Add the below content in index.js.

```
exports.handler = (event, context, callback) => {
    const { instanceId, instanceRegion, instanceType } = event;
    
    const ec2 = new AWS.EC2({ region: instanceRegion });
    
    Promise.resolve()
        .then(() => ec2.stopInstances({ InstanceIds: [instanceId] }).promise())
        .then(() => ec2.waitFor('instanceStopped', { InstanceIds: [instanceId] }).promise())
        .then(() => ec2.modifyInstanceAttribute({InstanceId: instanceId, InstanceType: { Value: instanceType } }).promise())
        .then(() => ec2.startInstances({ InstanceIds: [instanceId] }).promise())
        .then(() => callback(null, `Successfully modified ${event.instanceId} to ${event.instanceType}`))
        .catch(err => callback(err));
};

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629571563778/XCkUQ6fFx.png)


- 
Then Configure test event.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629571608463/I3b9ynlsp.png)



Test events Content

```
{
  "instanceRegion": "ap-south-1",
  "instanceId": "i-07010f188bba51f72",
  "instanceType": "t2.micro"
}
``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629571667880/CwyLrFKUG.png)


> 
In the below test event values as your needed value.

- 
instance type (t2.micro)

- 
instance id (i-07010f188bba51f72)

- 
instanceRegion (ap-south-1)


- 
In the general configuration change the function execution time to 5 mins.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629572113329/C_FDKHOVy.png)

### 4.Test the Function


- 
Ok Now we will test the lambda function.


- 
Just click the test button.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629572078343/h4kM3oJa-.png)


**Yeahh its working perfectly.**

### 5.Schedule the The lambda function


> 
In the cloud watch console -> event ->  Rules -> Create Rules -> cron expression -> Schedule : 45 11 * * ? * 

> 
In the targets select Lambda function -> Configure Input -> Constant test -> input the test event value and create rule.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629573298994/xgWaRfBAc.png)

>**I Have tested this its perfectly work for me and changed the instance type as per the scheduled.**