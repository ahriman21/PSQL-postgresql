
## database intro

* database is a space to store data.

* we don't control database directly but we use dbms

* dbms : database management system's duty is to control and manage the transactions and manipulating data in database.




## normaliztion :
to standard your database design

* unf ==> not normalized tables


* 1nf ==> - each column got uniq name.  
          - order of columns or rows must not matter.  
          - each column must have a single data type.  
          - two rows can not contain same values.  
          - each column must contain a single value, dont split values by comma in  one column.  
          - columns can not have repeating values.  


* 2nf ==> - 1nf must be done.  
          - all none-key fields shoud depend on all key fields  


* 3nf ==> - 2nf must be done.  
          - none-key fields shouldn't depend to each other.(transitive dependency)  




## keys
* candidate key = when some fileds have the condition to be primary key we call them candidate key


* alternative key = when you pick one of the condidate keys as your primary key, the other ones are called alternative keys.


* super key = a field or a combonation of several fields which can identify a row uniquely.


* surrogate key = this is a unique key that it itself doesnot mean anything and defined by programmer like `state_id`. for instance in our `state` table we consider Texas as `1`. fields like state_id which we define it as primary key are surrogate.


* natural key = natural key is a field that has meaning in real world and also is unique and can identify rows, like `national_code` in table of `person`.
these fields that are unique and meaningfull in real world are natural keys.


* composite key = if we have two fields defined as one primary key .


