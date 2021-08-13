## How to Install and Configure Big Blue Button on Ubuntu 18

**BigBlueButton**

This  is an open source web conferencing system for online learning. That means


- 
**Open source **
                 
*You have full access to BigBlueButton’s source code under an open source license. With the source code, you can install, customize, develop, scale, and integrate it into your products and services with help from the community. Cool.*


- 
**Web conferencing system** 
                  
*BigBluebutton provides you all the core features you would expect from a commercial web conferencing system (but under an open source license) including real-time sharing of audio, video, presentation, and screen – along with collaboration tools such as chat (public and private), whiteboard, shared notes, polling, and breakout rooms. BigBlueButton can record your sessions for later playback.
*

- 
**Online learning **
                  
*BigBlueButton extends these core features for online learning. For example, a tutor can enable multi-user whiteboard to direclty work with a student on solving a math problem. BigBlueButton has deep integrations with all the major learning management systems (LMS). It also supports Learning Tools Interoperability (LTI) 1.0 for integration with other LMS systems.*



### **Available Features**
Big Blue Button contains all of the standard features one would expect from a video conferencing solution. The ability to share video and audio inputs as well as the ability to conduct presentations with a whiteboard functionality that allows for pointers and zooming as well as screen sharing. There are also text-based chat rooms that can be created in both public and private formats. And since BBB uses a pure HTML 5 client, the software can be used in most common web browsers available today. For these reasons, BBB is the obvious choice for users looking for an open source comprehensive video conferencing solution.


> 
In this article i am going to explain how to very simply install BigBlueButton Package on ubuntu server using the script file.



### 1. System requirements for Big Blue Button Test Environment


- 
Ubuntu 18.04

- 
8 GB of memory with swap enabled

- 
4 CPU cores, with high single-thread performance

- 
30 GB of free disk space (or more) for recordings


- 
250 Mbits/sec bandwidth (symmetrical) or more


- 
A hostname (such as bbb.example.com) for setup of a SSL certificate



### 2. Ports need to be open


**TCP **

- 
80
 

- 
443


- 
7443


- 
5066


- 
1935


**UDP**


- 
16384 - 32768


### 3. Enable Swap space
First we want to enable Swap Space for that . Basically This maganto server running many supported application's.

so we must enable swap space for that.

If you not aware how to enable swap space on linux instance check my other article.
Here. 👇


%[https://venket.hashnode.dev/how-to-enable-swap-space-on-aws-ubuntu-or-any-linux-servers]




### 4. Map the domain name

We need to map servers public IP to the domain name .domain name map to the public ip address in your domain registrar. That name is host name of the BBB server.

### 5. Installation Script Part

Now we are going to execute the script to download, install and configure the Big Blue Button package and its dependencies.


> 
In the below syntax section i have explain what is the values provides in the script.


**Syntax:** 


- 
To download the script = wget -qO- https://ubuntu.bigbluebutton.org/bbb-install.sh | bash -s 


- 
**-w**  installs the uncomplicated firewall (UFW) to restrict access to TCP/IP ports 22, 80, and 443, 
             and UDP ports in range 16384-32768
             
- 
**-a **  installs the API demos (making it easy to do a few quick tests on the server)


- 
**-v**   bionic-23 installs the latest build of BigBlueButton 2.3.x


- 
**-s**   sets the server's hostname to be bbb.shivam.com

- 
**-e**   provides an email address for Let's Encrypt to generate a valid SSL certificate for the host.


### **The Big Blue Button Installation Script**

```
wget -qO- https://ubuntu.bigbluebutton.org/bbb-install.sh | bash -s -- -w -a -v bionic-23 -s bbb.shivam.com -e venket@shivammail.com

``` 

Just copy paste and hit enter... Relax your self or go for a coffee... It will take 15 minutes to install...

That's All Guys.... We done the installation.


