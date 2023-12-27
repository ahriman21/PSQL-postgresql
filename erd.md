## what is ERD ?
entity relationship diagram displays how a system or databases work.

## main shapes 
* rectangle = entity - anything we want to know about.
    * double bordered rectangle = week entities - a week entity lose its meaning if a parent entity doesnot exist.
    * filled rectangle = external data.
* diamond = a relation between two entity.
    * double bordered diamond = week relationship - when a parent entity could have 0 week entities.
* circle = attributes of an entity.
    * dotted circle = week attribute
    * double bordered cirlce = if an attribute includes other attributes inside itself.

## relations
* one-to-one = (1:1)
* one-to-many = (1:N)
* many-to-many = (M:N) or (N:N)
