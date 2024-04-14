## tech stack
- php
- on admin'
```
: SQLite3::prepare(): Unable to prepare statement: 1, near "testpass123": syntax error in
/var/www/html/login.php
on line
17

No hacking please


```
- so it is not having issue with username but with password i.e ' is not affecting username but password
- may be a comment would be useful
```

now tried
admin'/*
User not found or no cookie value associated with the user.
```

- which means it is trying to fetch that user
- for a random user name with same injection it says
- `login failed. Please check your username and password.`
- when passwod is set to `0` it says`Please enter both username and password.`
- 
```
admin' OR 1=1'/*
looks like it is using prepared stmts for username
```
