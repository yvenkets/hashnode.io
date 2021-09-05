## AWS Data Lifecycle Manager - To Automate EC2 AMI Backup

**AWS LifeCycle Manager - THe complete Backup solution for Your EC2 instance
**### 

You can use Amazon Data Lifecycle Manager to automate the creation, retention, and deletion of EBS snapshots and EBS-backed AMIs. When you automate snapshot and AMI management, it helps you to:


- 
Protect valuable data by enforcing a regular backup schedule.


- 
Create standardized AMIs that can be refreshed at regular intervals.


- 
Retain backups as required by auditors or internal compliance.


- 
Reduce storage costs by deleting outdated backups.


- 
Create disaster recovery backup policies that back up data to isolated accounts.


> 
When combined with the monitoring features of Amazon CloudWatch Events and AWS CloudTrail, Amazon Data Lifecycle Manager provides a complete backup solution for Amazon EC2 instances and individual EBS volumes at no additional cost.


> 
I will explain here how to automate backup of our ec2 instance as AMI backup.

### **Automate EC2 AMI Backup**


- 
In the EC2 console go to LifeCycle Manager under Elastic block store
section.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630655929796/GlMmWqb_E.png)


- 
Then goto create lifecycle policy section.click the drop down it have 3 options.


- 
EBS Snapshot Policy

- 
EBS-Backed AMI Policy

- 
Cross Account copy event policy

**I am selecting EBS-Backed AMI Policy.
**
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630655981030/W0WVsxFFf.png)


- 
Before that check the TAG of your EC2 instance which one you want to take AMI Backup

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630656086270/BW_D5k0Ewu.png)


- 
In the Policy Select the Target resource type your instance TAG and its value and add.



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630656158247/uVKlOAnpv.png)


- 
Mention the AMI Decryption here.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630656315460/-ABhino9m.png)



- 
If you have custom Values for IAM role and Tagging options change here. otherwise leave it default options.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630656237335/X9-f1nXsD.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630656273395/RWkZYT9nQ.png)


- 
Configure Schedule for our AMI Backup policy


**Here you want to mention your custom values for the below fields.**


> 
Schedule Name 

> 
Frequency

> 
Every (Hours,Days,Week)

> 
Starting at (time)

> 
Retention type (how many copy of AMIs you want)



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630656713518/YBYK7sQIk.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630656747494/ojASUxd4q.png)


- 
Review and Create the policy
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630656764268/NggXnnsmF.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630656806769/BQkl0305_.png)


- 
Check after your Scheduled time in the EC2 AMI Section.
Your policy create the EC2 backup as AMI.
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630666015021/m7jj9vl7N.png)

**That's All Guys**