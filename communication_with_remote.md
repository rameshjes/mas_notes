## How to transfer files from local to remote machine and vice versa

 We Will use "SFTP" for this. 

 ### What is SFTP? 

 	FTP(file Transfer protocol) is a method to transfer files between two remote systems.

 	SFTP(SSH File Transfer Protocol or Secure File Transfer Protocol) is a separate protocol packaged with SSH that works in a similar way over a secure connection.

 	advantage is the ability to leverage a secure connection to transfer files and traverse the filesystem on both the local and remote system.

 ### SFTP vs FTP::

 In almost all cases, SFTP is preferable to FTP because of its underlying security features and ability to piggy-back on an SSH connection. FTP is an insecure protocol that should only be used in limited cases or on networks you trust.

 ### How to Connect with SFTP::

 By default, SFTP uses the SSH protocol to authenticate and establish a secure connection. Because of this, the same authentication methods are available that are present in SSH.

 ** To establish an SSH connection and then open up an SFTP session using that connection by using following command:

 	sftp username@remote_hostname_or_IP

 	It will ask for password to login in remote machine.

 ### Getting Help in SFTP::

 The most useful command to learn first is the help command. This gives you access to a summary of the SFTP help. You can call it by typing either of these in the prompt:

 	help     (display a list of available commands)

 ### Navigating with SFTP::

 We can navigate through the remote system's file hierarchy using a number of commands that function similarly to their shell counterparts.

 First, let's orient ourselves by finding out which directory we are in currently on the remote system. Just like in a typical shell session, we can type the following to get the current directory:

 	use "pwd" command

 	Returns current working in remote machine

 	use "ls" command to list contents

 	use "cd directory_name" to get inside directory

 ###  Transferring Files with SFTP::

 * **Transferring Remote Files to the Local System**

 If we would like download files from our remote host, we can do so by issuing the following command:

 	get remoteFile

  by default, the "get" command downloads a remote file to a file with the same name on the local file system.

 We can copy the remote file to a different name by specifying the name afterwards:

 	get remoteFile localFile

 The "get" command also takes some option flags. For instance, we can copy a directory and all of its contents by specifying the recursive option:

 	get -r someDirectory

 * **Transferring Local Files to the Remote System**

 Transferring files to the remote system is just as easily accomplished by using the appropriately named "put" command:

 	put localFile

 The same flags that work with "get" apply to "put". So to copy an entire local directory, you can issue:

 	put -r localDirectory

 Note::

 There is currently a bug in the versions of OpenSSH shipped with current Ubuntu releases (at least 14.04 to 15.10) that prevents the above command from operating correctly. Upon issuing the command above to transfer content to a server using the buggy version of OpenSSH, the following error will be given: Couldn't canonicalise: No such file or directory.

 To solve this:

 To work around this issue, create the destination directory on the remote end first by typing mkdir localDirectory. Afterwards, the above command should complete without error.

 source:: https://www.digitalocean.com/community/tutorials/how-to-use-sftp-to-securely-transfer-files-with-a-remote-server
