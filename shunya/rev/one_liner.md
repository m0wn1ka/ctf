## code
```
flag = "ƃŰŶŉůļźŞŷŭŪƄŰŘŰŧŖŔŦĦŨĬƀźōşŋůĲňĳźĖőƃũťũŸŪĞ"
# flag = [~(c^i)*(-1) + 261 for i, c in enumerate([ord(a) for a in flag[::-1]])]
# print((flag))
# flag=flag[::-1]
print("flag is ",flag)
ord_values=[]
for i in flag:
    ord_values.append(ord(i))
new_array=[]
ans=''
for i,x in enumerate(ord_values):
    value1=x-261
    value2=value1*-1
    value3=~(value2)
    value4=value3^i
    new_array.append(value4)
    ans=ans+chr(value4)
    print(chr(value4),end='')
print("ans",ans)
print("reverse is ",ans[::-1])
```
