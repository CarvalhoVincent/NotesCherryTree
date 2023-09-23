# 📂 SCP Copy

### How to Use SCP Command to Securely Transfer Files

Updated  May 30, 2020\
•4 min read

SCP (secure copy) is a command-line utility that allows you to securely copy files and directories between two locations.\
With `scp`, you can copy a file or directory:\
• From your local system to a remote system.\
• From a remote system to your local system.\
• Between two remote systems from your local system.

When transferring data with `scp`, both the files and password are encrypted so that anyone snooping on the traffic doesn’t get anything sensitive.\
In this tutorial, we will show you how to use the `scp` command through practical examples and detailed explanations of the most common scp options.

### SCP Command Syntax

Before going into how to use the `scp` command, let’s start by reviewing the basic syntax.\
The `scp` command syntax take the following form:

```bash
scp [OPTION] [user@]SRC_HOST:]file1 [user@]DEST_HOST:]file2
```

◇ `OPTION` - [scp options](https://linux.die.net/man/1/scp) such as cipher, ssh configuration, ssh port, limit, recursive copy …etc.\
◇ `[user@]SRC_HOST:]file1` - Source file.\
◇ `[user@]DEST_HOST:]file2` - Destination file

Local files should be specified using an absolute or relative path, while remote file names should include a user and host specification.\
`scp` provides a number of options that control every aspect of its behavior. The most widely used options are:\
◇ `-P` - Specifies the remote host ssh port.\
◇ `-p` - Preserves files modification and access times.\
◇ `-q` - Use this option if you want to suppress the progress meter and non-error messages.\
◇ `-C` - This option forces `scp` to compresses the data as it is sent to the destination machine.\
◇ `-r` - This option tells `scp` to copy directories recursively.

### Before you Begin

The `scp` command relies on `ssh` for data transfer, so it requires an ssh key or password to authenticate on the remote systems.\
The colon (`:`) is how `scp` distinguish between local and remote locations.\
To be able to copy files, you must have at least read permissions on the source file and write permission on the target system.\
Be careful when copying files that share the same name and location on both systems, `scp` will overwrite files without warning.\
When transferring large files, it is recommended to run the `scp` command inside a [screen](https://linuxize.com/post/how-to-use-linux-screen/) or [tmux](https://linuxize.com/post/getting-started-with-tmux/) session.

### Copy Files and Directories Between Two Systems with

### `scp`

#### Copy a Local File to a Remote System with the

#### `scp`

#### Command

To copy a file from a local to a remote system run the following command:

```bash
scp file.txt remote_username@10.10.0.2:/remote/directory
```

Where `file.txt` is the name of the file we want to copy, `remote_username` is the user on the remote server, `10.10.0.2` is the server IP address. The `/remote/directory` is the path to the directory you want to copy the file to. If you don’t specify a remote directory, the file will be copied to the remote user home directory.\
You will be prompted to enter the user password, and the transfer process will start.\
`remote_username@10.10.0.2's password:`\
`file.txt 100% 0 0.0KB/s 00:00`\
Omitting the filename from the destination location copies the file with the original name. If you want to save the file under a different name, you need to specify the new file name:

```bash
scp file.txt remote_username@10.10.0.2:/remote/directory/newfilename.txt
```

If SSH on the remote host is listening on a port other than the default 22 then you can specify the port using the `-P` argument:

```bash
scp -P 2322 file.txt remote_username@10.10.0.2:/remote/directory
```

The command to copy a directory is much like as when copying files. The only difference is that you need to use the `-r` flag for recursive.\
To copy a directory from a local to remote system, use the `-r` option:

```bash
scp -r /local/directory remote_username@10.10.0.2:/remote/directory
```

#### Copy a Remote File to a Local System using the

#### `scp`

#### Command

To copy a file from a remote to a local system, use the remote location as a source and local location as the destination.\
For example to copy a file named `file.txt` from a remote server with IP `10.10.0.2` run the following command:

```bash
scp remote_username@10.10.0.2:/remote/file.txt /local/directory
```

If you haven’t set a [passwordless SSH login](https://linuxize.com/post/how-to-setup-passwordless-ssh-login/) to the remote machine, you will be asked to enter the user password.

#### Copy a File Between Two Remote Systems using the

#### `scp`

#### Command

Unlike [rsync](https://linuxize.com/post/how-to-use-rsync-for-local-and-remote-data-transfer-and-synchronization/) , when using `scp` you don’t have to log in to one of the servers to transfer files from one to another remote machine.\
The following command will copy the file `/files/file.txt` from the remote host `host1.com` to the directory `/files` on the remote host `host2.com`.

```bash
scp user1@host1.com:/files/file.txt user2@host2.com:/files
```

You will be prompted to enter the passwords for both remote accounts. The data will be transfer directly from one remote host to the other.\
To route the traffic through the machine on which the command is issued, use the `-3` option:

```bash
scp -3 user1@host1.com:/files/file.txt user2@host2.com:/files
```

### Conclusion

In this tutorial, you learned how to use the `scp` command to copy files and directories.\
You may also want to set up an [SSH key-based authentication](https://linuxize.com/post/how-to-setup-passwordless-ssh-login/) and connect to your Linux servers without entering a password.\
If you are regularly connecting to the same systems, you can simplify your workflow by defining all of your connections in the [SSH config file](https://linuxize.com/post/using-the-ssh-config-file/) .\
