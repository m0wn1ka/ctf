```
>>> a='radha mounika'
>>> a_hex=a.encode().hex()
>>> a_decode=bytes.fromhex(a_hex)
>>> a_decode
b'radha mounika'
>>> final_a=a_decode.decode()
>>> final_a
'radha mounika'
>>> a==final_a
True
>>>
```
