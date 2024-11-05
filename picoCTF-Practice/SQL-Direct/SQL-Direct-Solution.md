# SQL Direct
Liam Reidy

**Instructions:** Connect to this PostgreSQL server and find the flag!

I'm surprised this was a "medium" difficulty challenge. When I connected to the server, it informed me that it was using `PostgreSQL`. It started in the SQL shell, so of course bash commands wouldn't work. I looked up how to view the tables in PostgreSQL, and found the command `\dt`. Using that command revealed the following:

```
pico-# \dt
         List of relations
 Schema | Name  | Type  |  Owner   
--------+-------+-------+----------
 public | flags | table | postgres
(1 row)
```

Then selecting all the data from that table:

```
pico=# select *
pico-# from flags;
```

```PostgreSQL
 id | firstname | lastname  |                address                 
----+-----------+-----------+----------------------------------------
  1 | Luke      | Skywalker | picoCTF{L3....4c0}
  2 | Leia      | Organa    | Alderaan
  3 | Han       | Solo      | Corellia
(3 rows)
```
