## Install Amazon Linux 2 on on-premises

Amazon Linux 2 is amazon's own Linux distribution. Its available on amazon cloud services(AWS) as vm.
here we are going to install Amazon Linux on our on-premises.



First we decide which virtualization platform we are going to use for this installation.

here you can go to download the vm image for all the virtualation platforms.

1.  [VMWare](https://cdn.amazonlinux.com/os-images/2.0.20210617.0/vmware/) 
2.  [KVM](https://cdn.amazonlinux.com/os-images/2.0.20210617.0/kvm/) 
3.  [Oracle VirtualBox](https://cdn.amazonlinux.com/os-images/2.0.20210617.0/virtualbox/) 
4.  [Microsoft Hyper-V](https://cdn.amazonlinux.com/os-images/2.0.20210617.0/hyperv/) 

Here we are going to download the amazon Linux 2 image.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1625816386759/wkJlO5j0F.png)

open vmware application and open and point out downloaded amazon linux 2 ovf images.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1625816965668/jffwvOv0y.png)

and import

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1625816901997/LwNEqp5_V.png)

now start the vm

in the os kernal selection mode press the e button to edit the kernal

and add this line


```
   rw  init = /sysroot/bin/sh

``` 



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1625822212051/eOFTTDFfh.png)

Ctrl+X

now your os enter in to single user mode

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1625822342757/2pgit7L9-.png)



then give the below commands



```


:/# chroot /

:/# passwd root

:/# touch /.autorelabel

:/# exit

``` 

Now the password reset part is done.

now you can able to login your amazon linux onpermises server


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1625823220581/bt-B_oBGz.png)

to enable password authentication through ssh edit the below file

sudo vi /etc/ssh/sshd_config

add this line


```
    password authenticaton yes

``` 


if you want allow root login through ssh add the below line


```
    permit root login yes

``` 




