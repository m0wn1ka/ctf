```
import random
import string
seed1='CVE-2022-42269'
seed1='202242269'
seed1='CVE-2022-42269'
seed1=7.9
seed1=202242269
random.seed(seed1)
allowed_chars = string.ascii_letters + string.digits
key = ''.join(random.choices(allowed_chars, k=43))
# print("key si ",key,"len is ",len(key))
c='5e04610a22042638723c571e1a5436142764061f39176b4414204636251072220a35583a60234d2d28082b'
#after applying bytes.fromhex()
value1=bytes.fromhex(c)
#after decodig to asci from bytes
value2=value1.decode()

# print("value2 is ",value2,"len is ",len(value2))#43
ans=''
for i in range(len(value2)):
    x=chr(ord(value2[i])^ord(key[i]))
    ans=ans+x
# print("ans is ",ans)
# print("rev is ",ans[::-1])
print("ans ",ans)
```
