## Install and configure GitLab CE on On-premises Server

GitLab is a web-based DevOps lifecycle tool that provides a Git repository manager providing issue-tracking and continuous integration and deployment pipeline features, using an open-source license, developed by GitLab Inc.
GitLab CE (Community Edition) - self-hosted, free and support from the Community forum.

Here we are going to install GitLab server on our on-premises server.

**Prerequisites**
- Ubuntu 18.04 Server
- Min RAM memory 4GB - for better performance, use 8GB
- Root privileges

What we are going to do
Upgrade our os
Install and configure openssh ,ca certificates,postfix,gitlab,letsencrypt
reset root password for gitlab

Update and upgrade os

```
    sudo apt update
    sudo apt upgrade -y

```

Install openssh and postfix services
```
    sudo apt install curl openssh-server ca-certificates postfix -y

``` 
During this screen its asks post fix configuration give internet site and 
mail domain  name in the next screen.

Download GitLab packages


```
    curl -sS https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash

``` 
 
Install the packages you download


```
     sudo apt install gitlab-ce -y

``` 

After the installation change the URL and give the domain name you going to be used


```
     sudo vim /etc/gitlab/gitlab.rb

``` 

in this file change the external URL line


```
external_url 'https://git.venketraman.com'

``` 

that same file change the lets encrypt section enable lets encrypt as true and give the lets encrypt contact mail address


```
letsencrypt['enable'] = true
letsencrypt['contact_emails'] = ['admin@example.com']

``` 



install lets encrypt using this command


```
    sudo apt install letsencrypt -y

``` 

after that reconfigure the gitlab using the below command


```
    sudo gitlab-ctl reconfigure

``` 

After all this u got the GitLab home screen as your configured domain name


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1625853040191/jXDU8DhFq.png)

if you want to reset user name and password means execute the below command

its asking username and password



```
    sudo gitlab-rake "gitlab:password:reset"  

``` 

Final steps

Now we are going to allow the required ports in firewall and enables it.

Using this commands you can allow the required**** protocols


```
    sudo ufw allow ssh
    sudo ufw allow http
    sudo ufw allow https

``` 

Enable the firewall on system startup


```
    sudo ufw enable  

``` 



