### what are the default databases in sql server ?
```
masterdb :
Master database is system database. It contains information about server's configuration.Without Master database, server can't be started.
it is used to store information of all the databases on the SQL server.

MSDB :
it is used for database backups, DTS packages, SQL Agent information, SQL Server jobs.

TEMPDB Database :
It stores temporary objects like temporary tables and temporary stored procedure.
This is a temporary database used to store temporary tables, cursors, indexes, variables .

Model Database :
It is a template database used in the creation of new database.
```

### what is DTS :
```
it stands for data transformation services.  is a Microsoft database tool with a set of objects and utilities to allow the automation of extract, transform and load operations to or from a database.
```

### sql agent :
```
SQL Server Agent is a Microsoft Windows service that runs scheduled administrative tasks that are called jobs
```

### collation :
```
In database systems, collation specifies how data is arranged and compared in the database. For example, Collation specifies how the database behaves against uppercase and lowercase letters, as well as how to recognize and deal with accents.
```

### Compatibility  version :
```
 In SQL Server, the compatibility level is a database-specific setting that determines how the database behaves in terms of syntax, behavior, and features. It allows you to run a database on a specific version of SQL Server, even if you are using a newer version of SQL Server.
 SQL Server has evolved over the years with each new version introducing new features, syntax, and behaviors. By setting the compatibility level of a database to an older version, you can ensure that the database will behave as it did in that specific version.
 When you have an old database that only runs in older versions of sql server, you can specify the older version. 
```
