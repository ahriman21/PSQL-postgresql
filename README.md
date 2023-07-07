# psql cheatsheet
a cheatsheet about psql commands (postgresql commands)

## Run psql :
```
psql
```


#### Run psql with a specifiec user :
```
psql  -U  username
```


#### run psql with specifiec user and also connect to a database in local machine :
```
psql  -U  username  -d  db name
```


## To see guid of psql commands :
```
psql --help
```  
```
\?
```


## To see guid of sql commands :
```
\h
```


## Display users of postgresql :
```
\du
```


## To see list of databases :
```
 \l 
``` 


#### To see list of databases with more detail :
```
\l+
```

## To see details of a table in an extended way :
```
\x
```


## to see details of a database (to see tables of a database) :
```
\dp
\dt
\d
```


## to see detail of a relation (detail of a table) :
```
\d  'relation name' 
```


## to copy a database:
```
CREATE  DATABASE  'new db  name'   TEMPLATE    'another database name you wanna copy from.'
```


## create user (role) in psql :
```
CREATE  ROLE  username   WITH
LOGIN
SUPERUSER
CREATEDB
CREATEROLE
VALID UNTIL  '2023-08-04'
PASSWORD 'xxxxxx' ;
```


## delete a user :
```
DROP  ROLE   "username" ;
```


## modify a user | edit a user | edit a role | modify a role:

* to remove a privilege | to remove a permission  we can use 'NO' before that permission without any 'space'.
```
alter  role  "user name"  NOSUPERUSER;
```

* add a privilege | add a permission :
```
alter  role  "user name"   'permission';
```


* change password of current user :
```
\password   "user name";
```


* change password of another user :
```
ALTER   ROLE/USER   'username'   WITH   PASSWORD  'new password';
```


## group | how to create group :

* to create groups , we use CREATE   ROLE   "group name"   NOLOGIN;
```
CREATE   ROLE   "group name"   NOLOGIN;
```


* add a user to a group :
```
ALTER  GROUP  'group'  ADD  USER  'user' ;
```


* remove users  from groups :
```
ALTER  GROUP  "group name"  DROP  USER  "username" ;
```


## ACL | access controll list | how to give a user a privilege on a table  ?

* syntax for GIVING  privilege :
```
GRANT  "access control"   ON    "table name"    TO   "username";
```

* example :
```
GRANT select ON  customers TO jack ;
```

* syntax for REMOVING  privilege :
```
REVOKE  "access control"  ON   "table name"   FROM  "user name" ;
```




