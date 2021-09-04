## How to Reset Amazon Web Console Password from Amazon CLI.

**Amazon web services have both GUI and CLI methods for user access.**


- 
Web console is GUI mode all of using and well known method.


- 
CLI is the most useful and best way to simplify our work on AWS.
We can simple run the scripts to manage our AWS resources using AWS CLI

**Here i am going to explain the below things.**


- 
Install AWS CLI


- 
Create IAM User and get credentials


- 
Configure our AWS account using credentials


- 
Verify the AWS CLi configuration


- 
Update or modify our AWS Webconsole password via AWS CLI




### 1.Insatll and configure AWS Cli

```
msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi

```
To verify your installation check the aws version command


```
aws --version

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630765504816/jylwSDNoG.png)
 

### 2. Create IAM User and get credentials


- 
Open IAM Console And Add user


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630764860316/axySuN3cL.png)



- 
Provide the appropriate rights to the user


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630764899230/FsDTJl5Bl.png)


- 
After create the user download the security credentials(Access Key ID ,Secret access key)
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630764950434/PMMVIunyL.png)

### 3. Configure our AWS account using credentials


- 
Now we are going to configure our IAM user in our local pc using **aws configure ** command

```
aws configure

``` 



- 
Now its asking Access Key ID ,Secret access key,Default region and out put file format.
 just enter your values

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629743439188/DDp6xc5ro.png)

### 4. Verify the AWS CLi configuration


- 
To verify your IAM configuration is working execute the below command.


```
aws s3 ls

``` 

- 
If you have any bucket on S3 it display the list of buckets you have.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629743570451/BF8DPy6tC.png)


### 5. Update or modify our AWS Web Console password via AWS CLI


> 
Syntax: aws iam update-login-profile --user-name (your iam user name) --password (your IAM new password)

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629743969954/pnqULNwFD.png)


- 
Now the web console password has changed.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629660491542/Ntb0yc6cU.png)

That's All Guys...