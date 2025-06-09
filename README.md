P7---

open Ubuntu 
type: 

1.sudo adduser shrujana
it will ask password give any you want
if again new password asked give that only same password.
press enter for everything don't give anything 

2.ssh -keygen
  y
 enter
3. sudo apt update 
4. sudo apt install ansible -y
5. ansible --version 
6. vi inventory.ini
    now the blank page will come in that at first line type
    localhost ansible_connection=local
    at last line 
    :WQ
    (it will come to terminal)
 7. ansible-inventory -i inventory.ini --list
 8. ansible all -i inventory.ini -m ping
 9. nano basic_playbook.yml
 now the blank page will open in that type

---
name: My First Playbook
        hosts: all
        tasks:
name: Print a message
                ansible.builtin.debug:
                msg: "Hello from Earth!”

after typing this ctrl+o
                  enter 
                  ctrl+x

10. ansible-playbook -i inventory.ini basic_playbook.yml
11. nano basic_playbook.yml                  

👉in that page type this
---
name: Create a directory
hosts: localhost
tasks:
name: Create the 'my_test_directory'
ansible.builtin.file:
path: /tmp/my_test_directory
state: directory

after typing this ctrl+o
                  enter 
                  ctrl+x 

12. ansible-playbook -i inventory.ini basic_playbook.yml                  
13. ls /twp




P8----

cmd> wsl --install 

In Microsoft store, install Ubuntu 22.04 LTS,   Create username and password 


Now open Ubuntu 

sudo apt update && sudo apt upgrade -y
sudo apt install openjdk -17 -jdk -y
java --version 
sudo apt install maven-y
mvn -- version 
sudo apt install git-y
git --version 
sudo apt update
sudo apt install ansible -y
ansible --version

ssh-keygen -t rsa -b 4096
hostname -I
ssh (username that we given Ubuntu) @(ip add)
ssh-copy-id (username) @ipadd
password type that we given at first to Ubuntu 

open Jenkins http://localhost:8080
in manage Jenkins,plugin,available plugin, there download Maven Integration Plugin and  SSH Agent Plugin 
now check whether it is enabled in install plugin 


new item ,give name,freestyle project, ok

go to github open Maven Project then copy link it will be at the code 

then in Jenkins go to general, in description box type >(given name) Artifacts

source code management, click git,in repo url paste the github repo link

credentials:  .....(github)>select the one like this 

branch is master

add build steps, select Execute windows batch command, there will be box ,type:
 cd %WORKSPACE%
 mvn clean package

build,add build steps, execute shell script on remote host using ssh

in ssh site ,fill box

 how to appear that at box first: manage Jenkins, system, ssh remote host ,there in credentials 
add ,give username Jenkins du password also, 
id type whatever you want 
click check connection 
Apply

dashboard, configure 

command box type:
scp "C:/Users/(give Jenkins username here)/.jenkins/workspace/(new item name)/target/*.jar"
(Ubuntuuname)@172.27.158.79:/home/ronnie/deployment/
ssh (Ubuntu uname) @172.27.158.79 "ansible-playbook /home/(Ubuntu uname)/ansible-deploy/deploy.yml"


go to Ubuntu terminal 
mkdir -p /home/(Ubuntu uname)/deployment
nano /home/(Ubuntu uname)/ansible-deploy/deploy.yml
ls
cd ansible -deploy/
ls
cat deploy.yml 
now build then click console output
ls
cd deployment/
ls
java -jar ,press tab, 


yaml script :

 ---
 - hosts: localhost
   tasks:
 - name: Ensure deployment directory exists
  file:
  path: /home/ronnie/deployment
  state: directory
  mode: '0755'

  - name: Copy the JAR file to the deployment folder
   copy:
   src: /home/ronnie/deployment/*.jar
   dest: /home/ronnie/deployment/