# SQL


![alt-текст](https://github.com/marynamarina/SQL/blob/master/SQL_1/Task_1.png "Task 1")

```SELECT t1.user_id, u.name AS user_name, t1.total_training_count, t2.max_training AS max_training_count_per_day
FROM (SELECT COUNT(user_id) AS total_training_count, user_id FROM training_details GROUP BY user_id) as t1
LEFT JOIN (SELECT COUNT(training_id) AS max_training, user_id, training_date FROM training_details GROUP BY user_id, training_date) AS t2
USING (user_id)
LEFT JOIN users AS u
ON t1.user_id = u.id
WHERE (t1.total_training_count > 2) AND (t2.max_training >1)
GROUP BY t1.user_id
ORDER BY total_training_count DESC
```

![alt-текст](https://github.com/marynamarina/SQL/blob/master/SQL_1/Solution_1.png "Solution 1")
