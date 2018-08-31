### mysql master slave replication demo

SO notes:

You could also use a stored procedure. Consider the following table as an example:

CREATE TABLE your_table (id int NOT NULL PRIMARY KEY AUTO_INCREMENT, val int);

Then you could add a stored procedure like this:

```
DELIMITER $$
CREATE PROCEDURE prepare_data()
BEGIN
DECLARE i INT DEFAULT 100;

WHILE i < 100000 DO
INSERT INTO your_table (val) VALUES (i);
SET i = i + 1;
END WHILE;
END$$
DELIMITER ;
```

When you call it, you'll have 100k records:

`CALL prepare_data();`

Many thanks to Tarun Lalwani for his excellent blog post
