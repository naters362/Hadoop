# Hadoop
1.	Open Bash on your local system
2.	Open git GitHub (create account if necessary) 
3.	Create a new Jupyter notebook repository on GitHub
4.	Move to bash 
5.	List the existing keys that might already be there with the command:
6.	# Ls ~/.ssh
7.	if no keys exist we are going to create them there will be two keys, one public key and one located on the local machine
8.	enter this code into the bash interface
9.	# mkdir -p .ssh
10.	Then we will generate the keys with the following code 
11.	Ssh-keygen
12.	We do not want to create a password just hit enter twice to create the keys
13.	The keys will act as the password
14.	We will then use the public key to help with generating access to GitHub and also access to a AWS 
15.	Type this code into Bash
16.	# cat ~/.ssh/id_rsa.pub
17.	copy this result that is returned and open your GitHub 
18.	move to settings in GitHub and open the SSH and GPG keys copy and paste in this section to create the key
19.	this should connect you to your GitHub and local computer using these keys that were just created
20.	go back to bash to make sure that the key is properly installed into GitHub type this into the bash command
21.	# ssh git@github.com
22.	This should allow you to access your GitHub through  bash 
23.	Next, we are going to puta copy of the public key on the desktop of the computer for easy access when setting up our AWS terminal
24.	To do this type this command into bash
25.	# cp ~/.ssh/id_rsa.pub ~/Desktop/
26.	this is just going to copy the key and connecting to your AWS a little easier
27.	now open amazon web services (AWS)
28.	first, we are going to put in the key just like we did in the GitHub instance
29.	first click on EC2 to bring you to the terminal home pages and then click on key pairs on the resources menu
30.	this should bring you to a key pair are and click on import key pair 
31.	 the key pair will be located on your Desktop because we saved it their open it in the open file area
32.	 This will have connected your key pair to the AWS account
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
45.	We are now going to access this machine through the bash on our local system
46.	Click on the instance information below the information of the instance and copy the public IP address located on the right side of the description
47.	 
