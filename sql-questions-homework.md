# SQL Homework

For this homework, we will use sqlite3, it is already available on your machine using the command `sqlite3`, copy the file sql_dump.sql in a folder where your sqlite3 database will be, then type:

```
sqlite3 wishlists.db < sql_dump.sql
```

This will create the database wishlists. Unlike Postgres, sqlite3 create a file in the folder where you are, if you delete this file, you delete the db !

To connect to the database, type `sqlite3 wishlists.db`, then you can execute sql statements.

Write SQL statements that:

    1. Selects the names of all products that are not on sale.
        SELECT name FROM products where on_sale = 'f';
            Teddy Bear
            Cat Ears
            Card Against Humanity
            Set of 12 Mason Jars
    2. Selects the names of all products that cost less than £20.
        SELECT name FROM products where price < 20.00;
            Teddy Bear
            The Ruby Programming Language
            Silicon Valley Monopoly
            Set of 12 Mason Jars
    3. Selects the name and price of the most expensive product.
        SELECT name, price FROM products order by price desc limit 1;
        SELECT name,  max(price) FROM products;
            Cat Ears|99.99
    4. Selects the name and price of the second most expensive product.
        SELECT name, price FROM products order by price desc limit 1, 1;
            Brown Leather Boots|82.0
    5. Selects the name and price of the least expensive product.
        SELECT name,  min(price) FROM products;
            Set of 12 Mason Jars|6.22
    6. Selects the names and prices of all products, ordered by price in descending order.
        SELECT name, price FROM products ORDER BY price DESC;
            Cat Ears|99.99
            Brown Leather Boots|82.0
            Lonely Pillow|78.82
            Card Against Humanity|25.0
            Hoodie|25.0
            Set of silverware|22.99
            The Ruby Programming Language|19.99
            Teddy Bear|17.99
            Silicon Valley Monopoly|10.99
            Set of 12 Mason Jars|6.22
    7. Selects the average price of all products.
        SELECT AVG(price) FROM products;
            38.899
    8. Selects the sum of the price of all products.
        SELECT SUM(price) FROM products;
            388.99
    9. Selects the sum of the price of all products whose prices is less than £20.
        SELECT SUM(price) FROM products WHERE price < 20.00;
            55.19
    10. Selects the id of the user with your name.
        SELECT id FROM users WHERE name = 'Tyrone Compton';
            9
    11. Selects the names of all users whose names start with the letter "J".
        SELECT name FROM users WHERE name LIKE 'J%';
            Jon Rogers
            James Gotsell
            Jonathan Anderson
    12. Selects the number of users whose first names are "Spencer".
        SELECT COUNT(name) FROM users WHERE name LIKE 'Spencer%';
            1
    13. Selects the number of users who want a "Teddy Bear".
        SELECT COUNT(product_id) FROM wishlists INNER JOIN products ON wishlists.product_id=products.id AND products.name = 'Teddy Bear';
            6
14. Selects the count of items on the wishlish of the user with your name.        
    
    15. Selects the count and name of all products on the wishlist, ordered by count in descending order.
        SELECT COUNT(product_id), name FROM wishlists INNER JOIN products ON wishlists.product_id=products.id GROUP BY products.name ORDER BY COUNT(wishlists.product_id) DESC;
            17|Hoodie
            16|Card Against Humanity
            15|Cat Ears
            9|The Ruby Programming Language
            6|Teddy Bear
            5|Silicon Valley Monopoly
            4|Brown Leather Boots
            2|Lonely Pillow
            2|Set of 12 Mason Jars
    16. Selects the count and name of all products that are not on sale on the wishlist, ordered by count in descending order.
        SELECT COUNT(product_id), name FROM wishlists INNER JOIN products ON wishlists.product_id=products.id AND products.on_sale = 'f' GROUP BY products.name ORDER BY COUNT(wishlists.product_id) DESC;
            16|Card Against Humanity
            15|Cat Ears
            6|Teddy Bear
            2|Set of 12 Mason Jars
    17. Inserts a user with the name "Jonathan Anderson" into the users table. Ensure the created_at column is set to the current time.
        INSERT INTO users (created_at, name) VALUES (strftime('%Y-%m-%d %H:%M:%S.%f','now'), 'Jonathan Anderson');
            15|2015-09-03 23:37:07.07.707|Jonathan Anderson
    18. Selects the id of the user with the name "Jonathan Anderson"?
        SELECT users.id FROM users WHERE name= 'Jonathan Anderson';
            15
19. Inserts a wishlist entry for the user with the name "Jonathan Anderson" for the product "The Ruby Programming Language".
20. Updates the name of the "Jonathan Anderson" user to be "Jon Anderson".
21. Deletes the user with the name "Jon Anderson".
22. Deletes the wishlist item for the user you just deleted.

Please supply SQL statements, and the results they generate.



###Hints
  - As with anything, if you get stuck, move on, then go back if you have time.
  - Don't spend all night on it!
  - Use the resources on teh internetz to solve harder ones - there are solutions to these questions that work with what we've learnt today, but other tools exist in SQL that could make the queries 'better' or 'easier'.
