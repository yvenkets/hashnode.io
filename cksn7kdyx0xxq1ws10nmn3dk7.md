## Schedule EC2 Power on and off using Windows task scheduler

**Hi Guys**,


> 
Here am going to explain how to create the Task in task scheduler. It will start and stop your ec2 instances in the scheduled time interval.

***Prerequisites***

**1.AWS Cli
2.IAM User with Ec2 Start and stop Rights
3.Configure AWS IAM user in your windows instance
4.create two batch files
5.Create the task in task scheduler
**

### 1.AWS CLI Tools installed in your  PC 


- 
Install it using this command.

```
msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi
``` 

- 
Verify the AWS Cli version in command line.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629633631429/HhbwqmKin.png)

### 2.IAM User with Ec2 Start and stop Rights


- 
Create the Policy with EC2 start and stop rights.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629633159999/Ac30vX7AY.png)

```
{
 "Version": "2012-10-17",
 "Statement": [
   {
    "Effect": "Allow",
    "Action": [
     "ec2:DescribeInstances",
     "ec2:DescribeInstanceStatus",
     "ec2:DescribeTags"
    ],
   "Resource": "*"
   },
    {
    "Effect": "Allow",
    "Action": [
     "ec2:StartInstances",
     "ec2:StopInstances",
     "ec2:RebootInstances"
    ],
   "Resource": "*"
   }
  ]
}

``` 


- 
Create the user and attach the policy


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629633288792/8fAnQYEK7.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629633327643/8qnOai5W6.png)


- 
Finally download the credentials.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629633422096/lSnwat6Uj.png)

### 3.Configure AWS IAM user in your windows instance


- 
Open your command line and type AWS Configure.


```
aws configure

``` 

- 
Its asks the Access key ID,Secret access key,region and default output format.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629633797299/KUWbX9uTa.png)


- 
Now you configured your AWS IAM user credentials in your pc.
to check for that execute the below command.


```
aws ec2 describe-instances --filters "Name=instance-state-name,Values=stopped"

``` 

- 
Its list the stopped state instances.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629634386507/TpM-gdvsu.png)


### 4.create two batch files


- 
Create two batch files stat instance and stop instance.



- 
To start the instance

```
aws ec2 start-instances --instance-ids i-0980fe3b109f08bc0

``` 


- 
To stop the instance

```
aws ec2 stop-instances --instance-ids i-0980fe3b109f08bc0

``` 

- 
Paste the content in notepad and save as .bat format.

### 5.Create the task in task scheduler



> 
Open task scheduler -> create basic task->select daily interval->select your time->start the program->select your start instance batch file ->and finish.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629635477866/U_z5mE-6x.png)

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629635500509/xYuwM06_8.png)

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629635525853/Wud6apJ2T.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629635563553/IyaPvv7Y7.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629635578211/Tt28FF2QN.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629635595796/j3VviwCHW.png)



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629635607452/98s9m8_o0.png)


> 
Do the same for stop instance task.

**I Have tested the scheduled time its working perfectly.**