## Host a Static website in GitHub Pages and map Your Domain Name

**Github**
GitHub is a code hosting platform for collaboration and version control.GitHub lets you (and others) work together on projects.

**Github Pages
**
GitHub Pages is a static site hosting service that takes HTML, CSS, and JavaScript files straight from a repository on GitHub, optionally runs the files through a build process, and publishes a website.


**Static Website
**
A static website uses server-side rendering to serve pre-built HTML, CSS, and JavaScript files to a web browser, in contrast to traditional dynamic sites that work by rendering the webpage at the time of the request.
Cost-efficiency is another reason companies migrate to a static site because static files are lightweight and often faster and cheaper to serve.


> 
Here I Am Going To demonstarte how host a static websontent in github repo and how to host and map with your Domain Name.


- 
First we want to upload Our Static Web contents to Github repository.


- 
I have created on new git repo and uploaded the content.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629278431940/QY2KEd3gq.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629278464545/1kmnYl7d8.png)



- 
Then go to settings and add the postfix ** github.io** to your repository name and rename it.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629278593877/aiOTZWH8r.png)


- 
On the settings console left pane select pages.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629278677996/YLAkS7PMx.png)


- 
Here you want to select which branch you want to host it.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629278790897/hLEsWQlyX.png)


- 
After saving that you get your github pages link.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629278863905/7DWLTup8j.png)


- 
You just open the link ... yeah your website content hosted online.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629278940339/Y3lOdOomM.png)

### Optional ( Map a Custom Domain Name)

**Domain Name  Registrar
**

A domain name registrar is a business that handles the reservation of domain names as well as the assignment of IP addresses for those domain names. Domain names are alphanumeric aliases used to access websites; for example, Google’s domain name is ‘google.com’ and their IP address is 192.168.1.1. Domain names make it easier to access websites without having to memorize and enter numeric IP addresses. 


**Some popoular DNS Resgirators**

- 
GoDaddy
- 
Namecheap
- 
Hostinger
- 
Route 53
- 
Freenom


If you alreday have domain name you just proceed next steps.
otherwise purchase it in godaddy or you can get the freedomain name in freenom.com.


> 
Freenom : grtting free domain name in freenom is tricky. if you have luck you can easily get. otherwise check it in the tricks to get frre domain name in youtube.




**I Am going to map the custom domain name in freenom.
**

- 
Open Freenom Domain Console

- 
Create 4  A Record point to the below IP Address.


```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629279548885/0nXSQbDxk.png)


- 
Then add one more record. create cname with the below your custom values


> 
Name  = www
>
Record type  =Cname
>
TTL = morethen 700
>
Value =  yvenkets.github.io. (Your github username.github.io)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629279979909/Nqacq2Eni.png)


- 
After add the records wait for 5 minutes for your records Sync all the domain servers globally.

- 
On GitHub pages add your domain name in that custom domain name field and save it.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629279658232/_FSc7Yr5r.png)


- 
Also check mark the enforce https option. so that your website server with https protocol.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629280568510/RC9uAj7C4.png)




- 
Yeah now you have successfully map your domain name. wait for 10 minutes for your domain get the SSL Certificate from GitHub.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629280756433/z34Qp0S0I.png)


- 
Now check your Domain Name in browser.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629280789465/42UCrO30u.png)

**Thats all guys.
**