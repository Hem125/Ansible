# Ansible
### Install Ansible on Ubuntu
- #### Login to Ubuntu system and run below apt commands to apply updates.
![Capture2](https://user-images.githubusercontent.com/103022040/178237593-80179cc8-7b5f-4236-ac0f-776e59564628.JPG)
- #### Install ansible dependencies by running the following apt command
![image](https://user-images.githubusercontent.com/103022040/178241476-db2a5c45-f6f6-403e-8e5f-d4d13a84f1ef.png)
- #### Once the dependencies are installed then configure PPA repository for ansible, run
![Capture1](https://user-images.githubusercontent.com/103022040/178238352-5005fea4-0e62-4fbe-a0d1-181a9db2f23c.JPG)
- #### Now we are ready to install latest version of Ansible on Ubuntu. Run following command
![Capture3 install ansible](https://user-images.githubusercontent.com/103022040/178238928-82d9ce45-80b7-4119-ab69-3d3b6a7a2d74.JPG)
- #### After the successful installation of Ansible, verify its version by executing the command
![image](https://user-images.githubusercontent.com/103022040/178240851-e1497711-dc53-42f7-9ab2-c5191481b98f.png)
- #### Because Ansible requires a Python interpreter (in order to run its modules), we need to install Python as well. For that, issue the command.
![Capture7](https://user-images.githubusercontent.com/103022040/178242299-a546b2bf-0e76-4abd-852a-9822fb78ca50.JPG)
### Setup SSH keys and share it among managed nodes
- #### Now let’s generate the SSH keys for sysops user from the control node and share it among managed hosts. Run  ssh-keygen command
![image](https://user-images.githubusercontent.com/103022040/178242653-3b2c294b-62f9-4f65-aa83-9dccd410db32.png)
- #### To share the ssh keys between control to managed hosts, run ssh-copy-id command example is shown below
![ssh copy id](https://user-images.githubusercontent.com/103022040/178243050-e74e2a71-235c-434d-8af0-4f2ddfcb6a7d.JPG)
- #### We have to make some change in ansible.cfg file
![image](https://user-images.githubusercontent.com/103022040/178245694-a3629679-3105-4f1b-99d3-8afb0edd2983.png)
- #### Need to set host checking to false
![image](https://user-images.githubusercontent.com/103022040/178246059-50cece08-6ba6-4763-9c78-4855e80464a1.png)
- #### To access the inventory file, use the following command in the control node’s terminal
![image](https://user-images.githubusercontent.com/103022040/178247400-d580491c-cac5-48df-9272-9959a648db47.png)
- #### Add the following section in host file
![image](https://user-images.githubusercontent.com/103022040/178247531-95182b18-4ac2-442d-a497-77c8dff7dade.png)
 - ##### To test the connection with the hosts, use the following command in the terminal on your control node
![image](https://user-images.githubusercontent.com/103022040/178255272-d164a820-b147-4d32-a7dd-840875ef4b8b.png)
- #### We can check the inventory file
![image](https://user-images.githubusercontent.com/103022040/178259659-52bba6c7-2f29-465f-ab8c-dce8616803f0.png)
### Playbook in Ansible
- #### Create a yml file using vi editor to create a playbook 
![image](https://user-images.githubusercontent.com/103022040/178264078-72c6b739-eb10-485b-8993-f2f2b4cd07fe.png)
- #### View the content inside the file 
![image](https://user-images.githubusercontent.com/103022040/178264744-934fc5df-d4c4-4db4-917e-e1c58bffa426.png)
- #### Run the following command to run the playbook 
![image](https://user-images.githubusercontent.com/103022040/178412988-b262b766-35d9-46c5-933e-69e5a254600f.png)
![ansibleplaybookrun](https://user-images.githubusercontent.com/103022040/178413087-6ebc560f-570e-4ad6-a341-8ab019efcf3d.JPG)
- #### lets run another playbook with following content
![image](https://user-images.githubusercontent.com/103022040/178416933-2bd61543-8d92-4a84-9dde-dd5aa903c42b.png)
- #### Playbook using run command shows the output in this format
![image](https://user-images.githubusercontent.com/103022040/178417503-a60a6fb5-3308-41cd-82df-4c4ae718f348.png)

Setup of Ansible

====================

1 Create 3 AWS ubuntu 18 instances

2 Name the 1st one as controller and remaining 2 as server1 and server2

3 Establish Passwordless ssh from Controller to Server1 and Server2

  a) Connect to server1 using git bash

  b) Setup password for the default user

     sudo passwd ubuntu

  c) Edit the ssh configuration file

     sudo vim /etc/ssh/sshd_config

     Search for "PasswordAuthentication" and change it from no to yes

  d) Restart ssh

     sudo service ssh restart

     Repeat the above steps from a to d on Server2 managed node

  e) Connect to Controller using git bash

  f) Generate the ssh keys

     ssh-keygen

  g) Copy the ssh keys

     ssh-copy-id ubuntu@private_ip_of_server1

     Repeat step g with ip address of Server2



4 Installing Ansible

  a) Update the apt repository

     sudo apt-get update

  b) Install software-properties-common

     sudo apt-get install -y software-properties-common

  c) Add the latest version of Ansible to apt repository

     sudo apt-add-repository ppa:ansible/ansible

  d) Update the apt repository

     sudo apt-get update

  e) Install ansible

     sudo apt-get install -y ansible



5 To check the version of ansible

  ansible --version



Ansible stores all the remote servers info in a file called as inventory file We should open this file and store the ip address of all the managed nodes here

sudo vim /etc/ansible/hosts

Here copy and paste the ip addresses of the managed nodes
