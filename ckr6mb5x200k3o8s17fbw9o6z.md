## Install IIS Server on Windows and secure with SSL

First we are going to install the Windows Internet information server role.

Inthe windows server open server manager and select add roles and features


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626294542961/GVOLL0hlX.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626294570239/aqm4KxzPy.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626294591362/5tKEfgP7d.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626294615139/qKIMsHtvw.png)

In the server role section select web server iis role

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626294715989/3HhS3RjCs.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626294767433/0s1nMm1md.png)

next features section dont select anything

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626294790283/e9g2efcZR.png)

Finall select install button and finish the iis role instalation



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626294900190/13TcWf-o7.png)



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626294917597/B0jQFFmil.png)



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626295096485/53fiQOTaj.png)


Now your iis role installed sucessfully.

Check your srvers public ip(local ip in lan)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626295227712/vgrDpJ1GG.png)


now you can see IIS default welcome page.

now we are going to map your public ip to your registered domain name in godaddy.

In Domain regiterar (go daddy,hostingar,route 53) control panel just add the record and give the below details.

Type : A (record)
Host : <ur domain name /subdomain name>
Value :<Your servers Public ip address>
TTL(Time to Live) : give minimum 10 mins

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626295401248/xd-gJm8Pu.png)

now check your domain name in browser.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626295571801/0o2XkvORn.png)

Now we are going to secure our website with SSL.

for that we are going to use free certificate provider let's encrypt.

first download the certbots installer for windows in the below link.

https://www.win-acme.com/

  [Download Here](https://github-releases.githubusercontent.com/46080325/682c6d80-dc18-11eb-8e56-22b06002da0d?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20210714%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20210714T205524Z&X-Amz-Expires=300&X-Amz-Signature=1e748edf2185cfbe6a950c8ee0f36642909ac6cb9111e58860e3b5bf487d46cd&X-Amz-SignedHeaders=host&actor_id=0&key_id=0&repo_id=46080325&response-content-disposition=attachment%3B%20filename%3Dwin-acme.v2.1.18.1119.x64.trimmed.zip&response-content-type=application%2Foctet-stream)


download and extract the package to c drive as win acme

now execute the winacme.exe 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626296317240/0xVynbvG6.png)

Select create new certificate N

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626296347901/6NFUkP1x_.png)


before that you want to verify your iis site bindings are properly configure below.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626296497569/Hjs9JV5rg.png)


Select your site name here.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626296579047/_1Pko6ah2.png)

Next choose All option


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626296670951/bR1vStDoj.png)


Its asking confirmation


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626296714453/LRgeFpcGp.png)

after that it download the end user license agrrement in your local server.

its asking to open default application.
press Y


After that its asks agree the terms

again press Y

After that its asks the mail for communication purpose.

enter your mail id.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626296821306/IIm7YktaB.png)


After that its successfully deploy the ssl certificate ffor your website.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626296968575/X3_P9nMdt.png)

Now check you website is secured with SSL.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626297348513/jeleOk6xI.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626297376684/UPxNpiy4ly.png)


forget to tell one thing always create new site in iis . so you not face any difficulties.
dont use default website.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626297922554/qynjfrBxf.png)
