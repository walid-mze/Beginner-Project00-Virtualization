## This file is a Markdown file where commands, configuration files and problems encountereed are stored.

after installing debian i setup the hostname as required : Walid.Mamze-CC
## SSH & Firewall Configuration ::
- install ssh :`sudo apt install openssh-server -y`
- go to the sshd configuration file : `sudo nano /etc/ssh/sshd_config`
- change the port : 1111 and PermitRootLogin no
- test it : `systemctl status ssh`
- it display : Feb 08 21:59:38 Walid.Mamze-CC sshd[3995]: Server listening on 0.0.0.0 port 1111.
- test if the root can log in : `ssh -p 1111 Walid.Mamze-CC@127.0.0.1`
- it displays : Permission denied, please try again.
- install ufw : `sudo apt install ufw -y`
- enable ufw  :  `/usr/sbin/ufw enable `
- allow just the 1111 port : `/usr/sbin/ufw allow 1111/tcp`

## User Management & Password Policy :
- add a new user Walid.Mamze : `useradd -m Walid.Mamze`
- edit the file /etc/login.defs : `nano /etc/login.defs`
- changed the expiration period , min number of days allowed before the modification of a password, and the warning 7 days before the expiration
- to ensure password rules as required in the readme instructions I added the line  `password requisite pam_pwquality.so retry=3 minlen=10 ucredit=-1 lcredit=-1 dcredit=-1 maxrepeat=3 reject_username ` to the file `/etc/pam.d/common-password`
- and add this line just for non root users (the paswd should be diff from prev by at least 7 characters ) :`password requisite pam_pwquality.so difok=7`
- to see all the users cat /etc/passwd
- note :(the first policy is not strictly applied for the root if we dont respect some rule we get just a warning)
- edit the sudoers file : `sudo visudo`
- add thoses lines :<br>
    #Enforce password policy<br>
Defaults        passwd_tries=3<br>
Defaults        badpass_message="Wrong password, try again. by Root: Walid"<br>

     #Save sudo logs  <br>
Defaults        log_output<br>
Defaults        logfile="/var/log/sudo/sudo.log"<br>



                  






  

