# TestingLinuxServer_Assessment
Testing, Linux and Server Assessment for Submission. Answers to all questions. Screen shots are attached in readme file.

#Link to locate on Git: https://github.com/titansumit007/TestingLinuxServer_Assessment.git



LAPTOP-6Q9E9RN9:/# #..... Starting project....
LAPTOP-6Q9E9RN9:/#
LAPTOP-6Q9E9RN9:/# #Create the directory /home/ec2-user/webapp/ with three subdirectories inside it: scripts/, logs/, an
d config/ using a single mkdir -p command.
LAPTOP-6Q9E9RN9:/#
LAPTOP-6Q9E9RN9:/# bash
LAPTOP-6Q9E9RN9:/# echo $0
bash
LAPTOP-6Q9E9RN9:/# mkdir -p /home/ec2-user/webapp/{scripts,logs,config}
LAPTOP-6Q9E9RN9:/# tree /home/ec2-user/webapp
/home/ec2-user/webapp
├── config
├── logs
└── scripts

<img width="1917" height="912" alt="SS1" src="https://github.com/user-attachments/assets/cbf9044d-c5b9-47e9-8314-0594e9a52feb" />



3 directories, 0 files
LAPTOP-6Q9E9RN9:/# cd /home/ec2-user/webapp
LAPTOP-6Q9E9RN9:/home/ec2-user/webapp# cd config

#Adding app.config and writing App_name & port.

LAPTOP-6Q9E9RN9:/home/ec2-user/webapp/config# cat > config/app.conf <<EOF
APP_NAME=WebApp
PORT=8080
EOF

bash: config/app.conf: No such file or directory
LAPTOP-6Q9E9RN9:/home/ec2-user/webapp/config# cd ..
LAPTOP-6Q9E9RN9:/home/ec2-user/webapp# cat > config/app.conf <<EOF
APP_NAME=WebApp
PORT=8080
EOF
LAPTOP-6Q9E9RN9:/home/ec2-user/webapp# cd logs
LAPTOP-6Q9E9RN9:/home/ec2-user/webapp/logs# touch app.log
LAPTOP-6Q9E9RN9:/home/ec2-user/webapp/logs# ls -l
total 0
-rw-r--r--    1 root     root             0 May 24 00:30 app.log
LAPTOP-6Q9E9RN9:/home/ec2-user/webapp/logs# cd ..

<img width="1917" height="977" alt="SS2" src="https://github.com/user-attachments/assets/260bdb71-03d4-4f31-a9ed-0a090ca65ce2" />

#Adding permissions:

LAPTOP-6Q9E9RN9:/home/ec2-user/webapp# chmod 755 scripts/

LAPTOP-6Q9E9RN9:/home/ec2-user/webapp# ## Owner can read, write, and execute, Group can read and execute only, Others can read and execute only

LAPTOP-6Q9E9RN9:/home/ec2-user/webapp#
LAPTOP-6Q9E9RN9:/home/ec2-user/webapp# chmod 644 config/app.conf
LAPTOP-6Q9E9RN9:/home/ec2-user/webapp# #Owner can read and modify the file, Group can only read the fil, Others can only read the file
LAPTOP-6Q9E9RN9:/home/ec2-user/webapp#
LAPTOP-6Q9E9RN9:/home/ec2-user/webapp# chown -R root:root /home/ec2-user/webapp/
LAPTOP-6Q9E9RN9:/home/ec2-user/webapp# ls -lR /home/ec2-user/webapp/
/home/ec2-user/webapp/:
total 3
drwxr-xr-x    2 root     root          1024 May 24 00:28 config
drwxr-xr-x    2 root     root          1024 May 24 00:30 logs
drwxr-xr-x    2 root     root          1024 May 24 00:13 scripts

/home/ec2-user/webapp/config:
total 1
-rw-r--r--    1 root     root            26 May 24 00:28 app.conf

/home/ec2-user/webapp/logs:
total 0
-rw-r--r--    1 root     root             0 May 24 00:30 app.log

/home/ec2-user/webapp/scripts:
total 0

<img width="1918" height="1017" alt="SS3" src="https://github.com/user-attachments/assets/4809d833-684f-4293-9094-190081996fdd" />

#Creating Script...

LAPTOP-6Q9E9RN9:/home/ec2-user/webapp# cd /home/ec2-user/webapp/scripts/
LAPTOP-6Q9E9RN9:/home/ec2-user/webapp/scripts# vi log_user.sh

#making executible file:
LAPTOP-6Q9E9RN9:/home/ec2-user/webapp/scripts# chmod +x log_user.sh

#verifying and tesing

LAPTOP-6Q9E9RN9:/home/ec2-user/webapp/scripts# ls -l log_user.sh

-rwxr-xr-x    1 root     root           210 May 24 01:09 log_user.sh

LAPTOP-6Q9E9RN9:/home/ec2-user/webapp/scripts# ./log_user.sh
Enter your name: Sumit
APP_NAME=WebApp
PORT=8080
Login: Sumit Date: Sun May 24 01:10:51 UTC 2026

LAPTOP-6Q9E9RN9:/home/ec2-user/webapp/scripts# ./log_user.sh
Enter your name: Shraddha
APP_NAME=WebApp
PORT=8080
Login: Sumit Date: Sun May 24 01:10:51 UTC 2026
Login: Shraddha Date: Sun May 24 01:11:15 UTC 2026

LAPTOP-6Q9E9RN9:/home/ec2-user/webapp/scripts# ./log_user.sh
Enter your name: Shreyna
APP_NAME=WebApp
PORT=8080
Login: Sumit Date: Sun May 24 01:10:51 UTC 2026
Login: Shraddha Date: Sun May 24 01:11:15 UTC 2026
Login: Shreyna Date: Sun May 24 01:11:51 UTC 2026

#verifying app.log file.

LAPTOP-6Q9E9RN9:/home/ec2-user/webapp/scripts# cat /home/ec2-user/webapp/logs/app.log
Login: Sumit Date: Sun May 24 01:10:51 UTC 2026
Login: Shraddha Date: Sun May 24 01:11:15 UTC 2026
Login: Shreyna Date: Sun May 24 01:11:51 UTC 2026

<img width="1918" height="947" alt="image" src="https://github.com/user-attachments/assets/09da7601-ec7a-4224-aa26-31ab467276c1" />


#verifying structure:

LAPTOP-6Q9E9RN9:/home/ec2-user/webapp/scripts# ls -lR /home/ec2-user/webapp/
/home/ec2-user/webapp/:
total 3
drwxr-xr-x    2 root     root          1024 May 24 00:28 config
drwxr-xr-x    2 root     root          1024 May 24 00:30 logs
drwxr-xr-x    2 root     root          1024 May 24 01:09 scripts

/home/ec2-user/webapp/config:
total 1
-rw-r--r--    1 root     root            26 May 24 00:28 app.conf

/home/ec2-user/webapp/logs:
total 1
-rw-r--r--    1 root     root           149 May 24 01:11 app.log

/home/ec2-user/webapp/scripts:
total 1
-rwxr-xr-x    1 root     root           210 May 24 01:09 log_user.sh

LAPTOP-6Q9E9RN9:/home/ec2-user/webapp/scripts#
LAPTOP-6Q9E9RN9:/home/ec2-user/webapp/scripts#




#Adding group Writers:

LAPTOP-6Q9E9RN9:/home/ec2-user/webapp/scripts# groupadd writers
LAPTOP-6Q9E9RN9:/home/ec2-user/webapp/scripts# cat /etc/group | grep writers
writers:x:1001:
LAPTOP-6Q9E9RN9:/home/ec2-user/webapp/scripts# cd ..
LAPTOP-6Q9E9RN9:/home/ec2-user/webapp# cd ..
LAPTOP-6Q9E9RN9:/home/ec2-user# cd ..
LAPTOP-6Q9E9RN9:/home# useradd -m devuser1
LAPTOP-6Q9E9RN9:/home# useradd -m devuser2
LAPTOP-6Q9E9RN9:/home# useradd -m devuser3
LAPTOP-6Q9E9RN9:/home# useradd -m devuser4
LAPTOP-6Q9E9RN9:/home# ls /home
devuser1  devuser2  devuser3  devuser4  ec2-user
LAPTOP-6Q9E9RN9:/home#
LAPTOP-6Q9E9RN9:/home#


LAPTOP-6Q9E9RN9:/home# #Add write-access users to writers group
LAPTOP-6Q9E9RN9:/home#
LAPTOP-6Q9E9RN9:/home#

LAPTOP-6Q9E9RN9:/home# usermod -aG writers devuser1
LAPTOP-6Q9E9RN9:/home#
LAPTOP-6Q9E9RN9:/home# usermod -aG writers devuser2
LAPTOP-6Q9E9RN9:/home#
LAPTOP-6Q9E9RN9:/home# groups devuser1
devuser1 writers
LAPTOP-6Q9E9RN9:/home# groups devuser2
devuser2 writers
LAPTOP-6Q9E9RN9:/home# #Change group ownership of the script
LAPTOP-6Q9E9RN9:/home#
LAPTOP-6Q9E9RN9:/home# chown root:writers /home/ec2-user/webapp/scripts/log_user.sh
LAPTOP-6Q9E9RN9:/home#


<img width="1908" height="998" alt="image" src="https://github.com/user-attachments/assets/7715f2b7-889b-4493-925c-e123649473ed" />


LAPTOP-6Q9E9RN9:/home# #Set permissions to 664
LAPTOP-6Q9E9RN9:/home#
LAPTOP-6Q9E9RN9:/home# chmod 664 /home/ec2-user/webapp/scripts/log_user.sh
LAPTOP-6Q9E9RN9:/home#
LAPTOP-6Q9E9RN9:/home# #Verify permissions
LAPTOP-6Q9E9RN9:/home#
LAPTOP-6Q9E9RN9:/home# ls -l /home/ec2-user/webapp/scripts/log_user.sh
-rw-rw-r--    1 root     writers        210 May 24 01:09 /home/ec2-user/webapp/scripts/log_user.sh
LAPTOP-6Q9E9RN9:/home#
LAPTOP-6Q9E9RN9:/home#
LAPTOP-6Q9E9RN9:/home# #Test write access (Allowed Users)
LAPTOP-6Q9E9RN9:/home#
LAPTOP-6Q9E9RN9:/home# su - devuser1
LAPTOP-6Q9E9RN9:~$ #appending text....test from devuser1
LAPTOP-6Q9E9RN9:~$
LAPTOP-6Q9E9RN9:~$ echo 'test from devuser1' >> /home/ec2-user/webapp/scripts/log_user.sh
LAPTOP-6Q9E9RN9:~$ exit
LAPTOP-6Q9E9RN9:/home# su - devuser2
LAPTOP-6Q9E9RN9:~$ echo 'test from devuser2' >> /home/ec2-user/webapp/scripts/log_user.sh
LAPTOP-6Q9E9RN9:~$ exit
LAPTOP-6Q9E9RN9:/home#
LAPTOP-6Q9E9RN9:/home#
LAPTOP-6Q9E9RN9:/home# #Test read-only users
LAPTOP-6Q9E9RN9:/home# su - devuser3
LAPTOP-6Q9E9RN9:~$ cat /home/ec2-user/webapp/scripts/log_user.sh
#!/bin/bash

read -p "Enter your name: " username

cat /home/ec2-user/webapp/config/app.conf

echo "Login: $username Date: $(date)" >> /home/ec2-user/webapp/logs/app.log

cat /home/ec2-user/webapp/logs/app.log
test from devuser1
test from devuser2
LAPTOP-6Q9E9RN9:~$ echo 'test from devuser3' >> /home/ec2-user/webapp/scripts/log_user.sh
-ash: can't create /home/ec2-user/webapp/scripts/log_user.sh: Permission denied
LAPTOP-6Q9E9RN9:~$ #write attempt:Denied......
LAPTOP-6Q9E9RN9:~$
LAPTOP-6Q9E9RN9:~$ exit

<img width="1915" height="993" alt="image" src="https://github.com/user-attachments/assets/37337f74-ca4a-4c72-937b-071d57429d86" />


LAPTOP-6Q9E9RN9:/home# su - devuser4
LAPTOP-6Q9E9RN9:~$ cat /home/ec2-user/webapp/scripts/log_user.sh
#!/bin/bash

read -p "Enter your name: " username

cat /home/ec2-user/webapp/config/app.conf

echo "Login: $username Date: $(date)" >> /home/ec2-user/webapp/logs/app.log

cat /home/ec2-user/webapp/logs/app.log
test from devuser1
test from devuser2
LAPTOP-6Q9E9RN9:~$ # Write Attept for devuser4
LAPTOP-6Q9E9RN9:~$
LAPTOP-6Q9E9RN9:~$ echo 'test from devuser4' >> /home/ec2-user/webapp/scripts/log_user.sh
-ash: can't create /home/ec2-user/webapp/scripts/log_user.sh: Permission denied
LAPTOP-6Q9E9RN9:~$
LAPTOP-6Q9E9RN9:~$
LAPTOP-6Q9E9RN9:~$ exit
LAPTOP-6Q9E9RN9:/home# ls -l /home/ec2-user/webapp/scripts/log_user.sh

<img width="1917" height="902" alt="image" src="https://github.com/user-attachments/assets/91c36a18-9922-45a0-bdf2-91c30cf086fd" />


-rw-rw-r--    1 root     writers        248 May 24 01:28 /home/ec2-user/webapp/scripts/log_user.sh
LAPTOP-6Q9E9RN9:/home#
