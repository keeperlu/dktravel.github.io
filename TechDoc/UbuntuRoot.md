### Enable Root User Account in Ubuntu
If for some reason, you need to enable the root account, you just need to set a password for the root user . In Ubuntu and other Linux distributions, you can set or change the password of a user account with the passwd command.

As a regular user in Ubuntu, you can only change your own password. The user you are logged in as must have sudo privileges to be able to set the root password.

To enable root account in Ubuntu, run the following command:

## sudo passwd root
You will be prompted to enter and confirm the new root password:
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
The password is not shown on the screen when you type it.
That’s it! You have successfully enabled the root account. You can now log in to your Ubuntu machine as user root using the new password.

Disable Root User Account in Ubuntu
If you previously enabled the root user in Ubuntu and now you want to disable it, set the root password to expire.

To disable the root account password, use the following command:
## sudo passwd -l root

### Sudo Users
Ubuntu users are encouraged to perform system administrative tasks by granting administrative privileges to a regular user using a tool named sudo. Sudo allows authorized users to run programs as another user, usually the root user.

By default on Ubuntu systems, members of the group sudo are granted with sudo access. The initial user created by the Ubuntu installer is already a member of the sudo group. Chances are that the user you are logged in as is already granted with administrative privileges.

If you want to grant sudo access to another user, simply add the user to the sudo group:
usermod -aG sudo username
To temporarily elevate root user privileges, run the command prefixed with sudo:

sudo some-command
The first time you use sudo in a session, you will be prompted to enter the user password.

If you want to run a command with sudo privileges without entering the password, you’ll need to edit the sudoers file. To do so type visudo:

sudo visudo
This will open the /etc/sudoers file with your favorite command line text editor . Add the following line by replacing username with your username:

/etc/sudoers
username ALL=(ALL) NOPASSWD: ALL
