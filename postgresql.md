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


* change password of user :
```
\password   "user name";
```

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


## type of tables :
* a)  logged  relations(reqular tables :  +persistency of data.   -lower speed.
* b)  unlogged relations : +high speed . -losign data by a system crush.
* c)  temp relations : one time used relations . in another hand  test relations.

* how  to  create  unlogged table  in postgres ?
```
CREATE   UNLOGGED  TABLE   "table name"() ;
```


## what are system catalogs | system catalog ?
system catalogs are the place to store metadata of databases . and a  system catalog structure is like a regular relation(tablel).
there are  some type of system catalogs such as : pg_database , pg_authid, pg_tables .

* exlaining some system catalogs :
* pg_database is a system catalog that stores data about all DBs that a postgres user created those.
* pg_authid is a system catalog that stores info about all postgres users.


* note : we can use system catalogs as we use regular databses . for example we can use
```
"select * from pg_authid"  command.
```


## What is template1 , template0 and postgres (when you run \l command ):
* template1 = every table that you create in postgres , is a copy of  "template1"  database and you can modify template1 attributes.
* postgres = the  "postgres"  database  includes informations of  "postgres" user .
* template0 = it is like template1 but it is not editable . you can not change its attributes or methods.


## index :
* add index to a column :
```
 CREATE  INDEX  'name of index'  ON  'table  name'(columns name)
```

* example :
```
CREATE   INDEX   username_indexing   ON   users   (username);
```

* delete index:
```
DROP  'name of index' ;
```


## view :
we can use 'view' ability in psql to call prewriten SQL commands . the functionality of this ability is similar to Procedures in sql.

* how to create a  view :
```
CREATE   VIEW   'view name' 
AS  
'your sql command' ;
```


* how to delete a view :
```
DROP  VIEW  'view name'  ;
```


* how to see list of your views :
```
\dv
```


* how to use views :
to use a view you can make a query on the view result (the usage is not like Procedure here) :
```
SELECT  *   FROM   'view name' ;
```


## log files | log system :
logs are text files that register system reports and events. there is no default place to save logs .
this is user's responsibility to define a place to store log files.

* to some settings for log files you should modify postgresql.conf file :
- there are some commented commands in this file you should Uncomment them :
```
log_destenation = 'stderr'
logging_collector= on  
log_directory = 'log'  # you can define a path .
log_file_name = '...'
log_timezone = 'Asia/Tehran'
log_statement = all
```

* to apply changes on your postgresql.conf  , you have to restart your postgres server :
in LINUX (this command is not used in psql , just in terminal):
```
pg_ctl -D /var/lib/postgres/data/ restart
```

in windows :
search for postgresql-[version] in services.msc in RUN and click on restart btn.


## backup | back up :
there is two ways to do it in postgresql logical backup and phisical backup.

* how to get a backup file  (this command is not used in the psql program just in terminal):
```
pg_dump  -U  [user]  -d [database]  -f   [path/database_backup.sql]
```

* how to restore backup :
if the bacup file was in sql format (use this command inside psql):
```
\i  [backup path and name]
```

you can use this command outside psql and only in terminal :
```
pg_restore  -U  [user]  -d  [database]  [backup name]
```


## connect to a database  :
* REMOTE
```
psql  -h  [host ip]  -U  [user]  -p  [port]   -d   [database name] ;
```

*example :
```
psql   -U   postgres   -d   postgres   -p   5432    -h   localhost ;
```

* LOCAL
 Connect to a database in psql :
```
 \c  'database name'
```


## how to create an auto increment and primary key field in postgresql :
```
CREATE  TABLE  [table name] (
id  SERIAL  PRIMARY  KEY
);
```


## date
* what is time stamp :
a data type including date and time .


* how to display current date using postgres functions :
```
NOW()::DATE;
```


* example :
```
CREATE   TABLE    test(
date_created   DATE   default   NOW()::DATE 
);
```


* subtract  or  add  dates :
to subtract one date from another :
```
SELECT  NOW()  -  INTERVAL('10  years');
```


* add  few  month  to date :
```
SELECT  NOW()  +  INTERVAL('5  months');
```


* get  only  year  out  of  DATETIME  value | DISPLAY  DATE:
```
# get day of month:
SELECT  EXTRACT(day  FROM  NOW());

# get day of  weak :
SELECT  EXTRACT(dow  FROM  NOW());
```

