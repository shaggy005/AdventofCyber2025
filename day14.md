# Containers - DoorDasher's Demise

## What exact command lists running Docker containers?
```
docker ps
```
## What file is used to define the instructions for building a Docker image?
```
Dockerfile
```
## What's the flag?
```
Last login: Sun Dec 28 19:42:08 2025 from 10.48.115.204
mrbombastic@tryhackme-2204:~$ docker exec -it uptime-checker sh

/ # 
/ # 
/ # whoami
root
/ # docker exec -it deployer bash

deployer@00c004221578:/app$ 
deployer@00c004221578:/app$ docker exec -it deployer bash
permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.50/containers/deployer/json": dial unix /var/run/docker.sock: connect: permission denied
deployer@00c004221578:/app$ 
deployer@00c004221578:/app$ sudo /recovery_script.sh

=== DoorDasher Recovery Script ===
Restoring original DoorDasher configuration...
Switching to DoorDasher skin (version 1)...
Copying version file to dasherapp container...
Successfully copied 2.05kB to dasherapp:/app/version.txt
Restarting dasherapp container...

dasherapp
Recovery complete! DoorDasher has been restored.
The hackers have been defeated!
deployer@00c004221578:/app$ cd /..
deployer@00c004221578:/$ ls
app  bin  boot  dev  etc  flag.txt  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  recovery_script.sh  root  run  sbin  srv  sys  tmp  usr  var
deployer@00c004221578:/$ cat flag.txt 
THM{DOCKER_ESCAPE_SUCCESS}
deployer@00c004221578:/$ 
```
```
THM{DOCKER_ESCAPE_SUCCESS}
```
## Bonus Question: There is a secret code contained within the news site running on port 5002; this code also happens to be the password for the deployer user! They should definitely change their password. Can you find it?
<img width="804" height="437" alt="image" src="https://github.com/user-attachments/assets/90c38453-ff1a-4fdb-b695-7694dfed9ec4" />

```
DeployMaster2025!
```
