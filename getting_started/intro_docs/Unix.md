# Unix basics

### Dialing into a remote server

Let's first get onto one of the Van Valen Lab's remote servers. If you don't know your username or the IP address of the server you're supposed to login to, one of the lab members can help you.

Windows users, use PuTTY to login to your server.

Linux and Mac users, put the following command in a terminal:
```bash
ssh -X -p [port] [your_username]@[server_ip_address]
```

### Directory Navigation

* List all files in current directory:  
```bash
ls
```


* Changing directory:  
```bash
cd [new_directory]
```


* Show name of current directory:  
```bash
pwd
```

### File Manipulation

* Copy a file:  
```bash
cp [original_filename] [new_filename]
```


* Make a new directory:
```bash
mkdir [directoy_name]
```


* Delete (remove) a file:
```bash
rm [filename]
```


* Delete (remove) a directory and all of its contents:
```bash
rm -r [directory_name]
```


* Change premissions of a file:
```bash
chmod [permissions] [filename]
```


* Change ownership of a file:
```bash
chown [username] [filename]
```

### Utilities

* To run a shell script:
```bash
./[scriptname.sh]
```
If this command throws an erorr, it's likely because you have permission issues. (Use `chmod` and/or `chown` to fix this.)


* To run a Python script:
```bash
python ./[scriptname.py]
```
Again, permission issues are a common source of error.


* To view all of the commands you've recently used that contain a certain string:
```bash
history | grep [string]
```


* To download a file from the internet, you hwave two options:
```bash
wget [URL]
curl [URL]
```


* To mount a remote filesystem on your computer:
```bash
sshfs -p [port] [your_username]@[server_ip_address]:[remote_directory] [local_mount_directory]
```
Errors? Again, permissions first.

### Special Characters

* `.` (a single dot) always represents the current directory. E.g.,
```bash
ls .
```
lists all files in the current directory.

* `..` (a pair of dots) always represents the parent directory of the current directory. E.g.,
```bash
ls ..
```
lists all files in the directory above the current directory.

### Special Command

If you're having permissions issues, you can prepend a given command with `sudo` and those pesky issues will almost certainly disappear. E.g., without sudo, the following command would be worthelss, since it would just return a permission error; with sudo, it will delete every single file on your server:
```bash
sudo rm -r /
```

WARNING! You can mess stuff up with `sudo`. We won't give you `sudo` privileges until you face a problem where you need them. At that point, come to us and we can give your account sudo privileges.
