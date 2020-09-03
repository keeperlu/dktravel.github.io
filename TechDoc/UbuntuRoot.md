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
