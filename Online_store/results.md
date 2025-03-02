### Users Table
```
mysql> select * from users;
+---------+---------------+-------------------------+---------------------+------------+----------------------+-----------+---------------------+
| user_id | username      | email                   | password_hash       | phone      | address              | user_type | created_at          |
+---------+---------------+-------------------------+---------------------+------------+----------------------+-----------+---------------------+
|       1 | john_doe      | john@example.com        | hashed_password     | NULL       | NULL                 | customer  | 2025-03-02 17:28:58 |
|       4 | Vaidik Namdev | john.doe@example.com    | hashed_password_124 | 9876543211 | 123 Main Streett, NY | customer  | 2025-03-02 17:50:21 |
|       5 | alice_smith   | alice.smith@example.com | hashed_password_456 | 9123456789 | 456 Elm Street, LA   | vendor    | 2025-03-02 17:52:04 |
|       6 | bob_martin    | bob.martin@example.com  | hashed_password_789 | 9234567890 | 789 Oak Street, TX   | admin     | 2025-03-02 17:52:04 |
|       7 | emily_clark   | emily.clark@example.com | hashed_password_321 | 9345678901 | 101 Pine Avenue, FL  | customer  | 2025-03-02 17:52:04 |
|       8 | david_lee     | david.lee@example.com   | hashed_password_654 | 9456789012 | 202 Maple Drive, CA  | vendor    | 2025-03-02 17:52:04 |
+---------+---------------+-------------------------+---------------------+------------+----------------------+-----------+---------------------+
```
