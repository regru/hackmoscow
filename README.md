###  [FOLLOW link to repo wiki for FAQ and instructions](https://github.com/regru/hackmoscow/wiki)


> _**NOTE**_: If you have any additional questions beyond this FAQ's - you may refer to the REG.RU desk or ask in Hack.Moscow Hackathon chat 
 


**Contents:**
* [VPS with GPU FAQ](#cloudgpu-faq)
* [CloudVPS FAQ](#instruction-for-cloud-servers) 
# CloudGPU FAQ

***

### How to login into server with SSH
 
```
ssh -A root@%vps_ip_address%
```
 
For example:
 
```
ssh -A root@85.17.45.19
```
 
### How to manage Docker
> _**NOTE**_: all Docker commands must be executed from the ~/tensorflowdocker folder
 
**login** into Docker container command line:
```
docker-compose exec tf bash
``` 
show Docker container **logs**:
```
docker-compose logs tf
``` 
**start** the jupyter-notebook container:
```
docker-compose up -d tf
``` 
**stop** the container:
```
docker-compose stop tf
```
**restart** the container:
```
docker-compose restart tf
```
 
### How to upload file(s) directly to the docker via the terminal
Upload file to the virtual machine by `scp` into ~/tensorflowdocker/data folder:
```
scp /path/to/file/on/localhost root@%vps_ip_address%:~/tensorflowdocker/data/
```
Or the same for whole folder:
```
scp -r /path/to/localhost/folder/ root@%vps_ip_address%:~/tensorflowdocker/data/
```
`~/tensorflowdocker/data/` already mounted into jupyter container, now you could find your data in `/opt/data` inside the container or from jupyter

 
### How to transfer files from VPS
This command shall download all data into the current directory on your localhost: 
```
scp -r root@%vps_ip_address%:~/tensorflowdocker/data/ .
```

**Second method**: install Midnight Commander file manager (mc) and login into VPS machine through the  
F9 menu -> Right -> Shell link… -> root@vps_ip_address%->enter password.  
Right pane of mc should list the VPS filesystem; selected files & folders could be copied with F5. Press TAB to switch between panes.  

![Кортинко](https://github.com/vilorij/hackmos/blob/master/1.png)

 
### How to manage Ubuntu packages in Docker
First login into Docker container:
```
cd ~/tensorflowdocker
docker-compose exec tf bash
```
Then from within the Docker container standard apt tools are available:
```
apt-get update && apt-get install %packagename%
apt-cache search %query%
```
 
### How to list available GPUs and NVIDIA driver version
Use NVIDIA SMI command line utility:
 
```
# nvidia-smi
Mon Oct  8 10:16:43 2018       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.72                 Driver Version: 390.72                    |
|-------------------------------+----------------------+----------------------+
```
 
 
### How to do all of above from within the Jupyter Notebook

To open Jupyter built-in terminal, locate an item “Terminal” in the top right “New” drop-down menu:
![Кортинко](https://github.com/vilorij/hackmos/blob/master/2.png)

To connect remote SSH servers from Jupyter Notebook Terminal, install and use ssh/scp tools:

```
apt install ssh
ssh root@%ip_address%
scp root@%vps_ip_address%:/path/to/file
```

> _**NOTE:**_ NVIDIA CUDA Toolkit and utilities are available from the Terminal.  
  
  
  
  
# Instruction for Cloud Servers 

***
For the VPS order follow the link: https://www.reg.ru/cloudvps/  

> _**NOTE**_: It is enough of one account per command.
> After creating the server, the letter with a root-password will be sent to the specified e-mail.

![_Завершение регистрации в облачных серверах_](https://github.com/vilorij/hackmos/blob/master/3.png)

 
 
After registration you will be taken to the servers management panel.  
Ignore the message «Your account is not protected enough». There is no need for this on Hackathon:

![_VPS control panel_](https://github.com/vilorij/hackmos/blob/master/4.png)

 
 
On the «Service's Balance» tab make sure that the bonus balance is equal to 250 bonuses. If there are no bonuses, **refer to REG.RU rack**: 

![Кортинко](https://github.com/vilorij/hackmos/blob/master/5.png)
_Вкладка «Баланс услуги»_
 
To create a server, push «Add server» button on «Servers» tab. There will be enough bonuses for three days of work of one Cloud-4 server or two Cloud-3 servers: 

![_Выбор параметров сервера_](https://github.com/vilorij/hackmos/blob/master/6.png)


If you need more resources, then you should reconsider the idea of your project.You can use applications, but make sure that the [set of incoming software](https://www.reg.ru/support/hosting-i-servery/oblachnie-serveri-vps/#expanders=c5) suits you.
 
After creating the server, copy the password and save it: 
![_Servers creating process_](https://github.com/vilorij/hackmos/blob/master/7.png)
 
 
Click on the server name and go to the server management page: 
![server management page](https://github.com/vilorij/hackmos/blob/master/8.png)

