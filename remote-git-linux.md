## Guide: Accessing GIT from Home using Linux


#### General Info
This guide assumes you are a CSCI student at VIU. The purpose of the guide is to explain how to access the git server behind the CSCI firewall. This is achieved by forwarding an unused port on your local machine to an address and port accessible on otter.

Note: Doing this will not affect your other git projects or using git with other servers such as github.

#### Steps to Access Git from Home:
1. Install git on your local machine
2. Copy RSA keys from otter
3. Modify the SSH config on your local machine
4. Forward local port to remote GIT server
5. Test Git!


#### Install Git on your local machine
Use one of the following commands to install Git.

  * Debian based distributions:
  
  `$ sudo apt-get install git`
    
  * Red Hat based distributions:
  
  `$ sudo yum install git`
    
  * Arch Linux:
  
  `$ sudo pacman -S git`
    
#### Copy RSA keys from otter
Now that git has been installed you need to copy `~/.ssh/csci` and `~/.ssh/csci.pub` to your local machine. There are many ways to do this but the simplest is probably to run the following command: (`scp` - [secure copy](http://linux.die.net/man/1/scp))

**Note: Replace USER with your CSCI Username.**

You can copy and paste the command or type it but make 
sure to include the double quotes around `”~/.ssh/csci*”`.

`$ scp USER@otter.csci.viu.ca:”~/.ssh/csci*” ~/.ssh`

#### Modify the SSH config on your local machine
Now that you have copied the RSA keys from otter you need to add the contents below to your local machines SSH config file. If the file does not exist you should create it using your prefered text editor. You need to change the port number to an unused port on your local machine above 1024. (port 1234 is used in the example)

Open / Create file with your prefered text editor (ex. vi)

`$ vi ~/.ssh/config `

Contents to be added:

````
Host csci
    HostName localhost
    Port 1234
    User csciadm
    IdentityFile ~/.ssh/csci
````

#### Forward local port to remote GIT server
Now that you have your local machine configured to connect with the git server, you will need to forward the local port specified in your SSH config to the git server address. In our case the CSCI git server address is cscidb.csci.viu.ca on port 22 and we are forwarding to this through otter. Run the following command in a new terminal windows to achieve this:

**Note: Replace USER with your CSCI username and 1234 with the port you chose to use in your SSH config file.**

`$ ssh -L 1234:cscidb.csci.viu.ca:22 USER@otter.csci.viu.ca`

*Every time* you want to access the remote server you will have to run this command in a separate terminal and leave it running until you are finished. You do not need to run this command for local `git` usage.

* Local Git Usage: `git add`, `git status`, `git commit`, `git stage`, etc
* Remote Git Usage: `git push`, `git pull`, `git clone`, `ssh csci fork`, `ssh csci info`, `git fetch`, etc.

#### Test GIT!
Test to see if you can access the git server. Open a new terminal and run the following command:

`$ ssh csci info`

If everything is working as expected you should see your git repositories on the CSCI git server.


#### Written By
  * Justin Pye [@j-pye](https://github.com/j-pye)



