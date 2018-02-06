This repository can be used to deploy your django project on remote server according to your desired needs. 

Things you need to change:
	
	-> Remote server address in hosts file
	
	-> If remote server is password less (if password is not asked after sudo command) then there is no need for ansible_sudo pass but if your remote server is not password less then change your password accordingly

	-> Change of the remote_user and become_user name in ansible.cfg file and the private file for the server. The private file for the server can be found in remote server /root/.ssh/ folder with the name of id_rsa and its public key file id_rsa.pub. In case of AWS just use the .pem file you got while creting your instance

	-> You can also change the order of performing tasks in deploy.yml file.

	-> I have used a preconfigured server so you have to make path according to your server architecture. Just remove /home/goplay_backend/ from everything and use your path by typing pwd on your remote server terminal

Roles: In roles i have configured what each playbook will do.

	-> Core- In core tasks/main.yml several tasks are performed and vars/main.yml just have the packages i want to be installed before it moves on to other playbooks.

	-> Every playbook in roles have same architecture. Taks main.yml contains the things that needs to be done and Vars main.yml have the variables which can be kept seperate in case you need to add more dependencies or you don't want to make them public like your dbname and dbpassword.

-> All this content have been gathered from different sources and you may find files empty because i encounterd some error or i didn't find it to be done immediately. Everything is quite simple. For git clone i used the username of bitbucket and password in url which is needed to be pass on while you start your ansible playbook. Keep in mind, to perform sudo taks you have to pass -s parameter with ansible command. I'm writing the command i used to deploy my project with bitbucket username and bitbucket password

ansible-playbook -s deploy.yml -e "githubuser=xxxxxxxxxxxx" -e "githubpassword=xxxxxxxx"

If you encounter any problem please use the -vvvv flag with the command