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
