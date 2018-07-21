 #Creating SSH keys 
1. Open Bash on your local system
2.	Open git GitHub (create account if necessary) 
3.	Create a new Jupyter notebook repository on GitHub
4.	Move to bash 
5.	List the existing keys that might already be there with the command:
6.	Ls ~/.ssh
7.	if no keys exist we are going to create them there will be two keys, one public key and one located on the local machine
8.	enter this code into the bash interface
9.  mkdir -p .ssh
10.	Then we will generate the keys with the following code 
11.	Ssh-keygen
12.	We do not want to create a password just hit enter twice to create the keys
13.	The keys will act as the password
14.	We will then use the public key to help with generating access to GitHub and also access to a AWS 
15.	Type this code into Bash
16. cat ~/.ssh/id_rsa.pub
17.	copy this result that is returned and open your GitHub 
18.	move to settings in GitHub and open the SSH and GPG keys copy and paste in this section to create the key
19.	this should connect you to your GitHub and local computer using these keys that were just created
20.	go back to bash to make sure that the key is properly installed into GitHub type this into the bash command
21.	ssh git@github.com
22.	This should allow you to access your GitHub through  bash 
23.	Next, we are going to puta copy of the public key on the desktop of the computer for easy access when setting up our AWS terminal
24.	To do this type this command into bash
25.	cp ~/.ssh/id_rsa.pub ~/Desktop/
26.	this is just going to copy the key and connecting to your AWS a little easier
27.	now open amazon web services (AWS)
28.	first, we are going to put in the key just like we did in the GitHub instance
29.	first click on EC2 to bring you to the terminal home pages and then click on key pairs on the resources menu
30.	this should bring you to a key pair are and click on import key pair 
31.	the key pair will be located on your Desktop because we saved it their open it in the open file area
32.	This will have connected your key pair to the AWS account
33.	Next, we are going to create some security, click on security groups in the EC2 dashboard
34.	Select all from the following and change from custom to anywhere  in the drop down menus
35.	Http, Custom TCP Rule (port range=5432), SSH, Custom TCP Rule (port range=27016), Custom RCP Rule (port range=443)
36.	Name the security group anything that you would like and activate it
37.	Go back to EC2 dashboard and click on create and Instance 
38.	We are now going to select the Server that we are going to use and the one that we want to use is an Ubuntu Server 16.04 (free tier) 
39.	Click on his server
40.	It will take you to choose instance type and for this purpose we are going to select a small sever t2.micro
41.	Hit next to configure instance details can make changes if need we won’t hit next
42.	Can select the Gib that you want to use on this machine up to 30 Gib is free 
43.	Hit next to configure security groups and select existing and choose the one that we made earlier
44.	Then hit next and launch the machine 
45.	A prompt will come up and ask you to use the key that we inserted into the AWS server click on that key to make sure that we use this key so we can log into the system
46.	We are now going to access this machine through the bash on our local system
47.	Click on the instance information below the information of the instance and copy the public IP address located on the right side of the description
48.	 Then we go into the local bash environment and type this code into the local bash to connect to the ubuntu server 
49.	ssh ubuntu@ <ip> ip= the local ip address that we just copied
50.	this will take you into the ubuntu server that we just created on AWS and should be displayed as ubuntu@############
51.	next we will load the jupyter shell into the bash session, so we can interact with jupyter in a web browser on the amazon server
52.	tmux 
53.	docker pull jupyter/datascience-notebook
54.	This will bring us into a tmux server, so we can interact in a docker environment
55.	docker run -d -p 443:8888 -v /home/ubuntu:/home/jovyan jupyter/datascience-notebook >.profile
56.	this will create a jupyter note book on the port 443. 
57.	Now we will go into a web browser to access this jupyter note book 
58.	Type the public ip address follow by :443 into the web browser and hit enter
59.	This will take you to a page prompting you for the token of the jupyter note book
60.	Go back into the bash setting to get the token for the jupyter notebook
61.	docker ps 
62.	docker exec (Container ID)
63.	this should display the token copy and paste it into the token area in the browser and hit enter
64.	after this you should have your fully running jupyter notebook on you aws instance

#SSH Picture

![alt text] (file:///C:/Users/Nate/Desktop/Introduction%20to%20data%20science%207-2018/SSh%20key%20picture.html)

#Server Costs

Price Per Hour
General Purpose - Current Generation 
m5=$5.914
m4=$2.831
m3=$2.71
