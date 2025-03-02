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
### Users Table
```
mysql> select * from products;
+------------+-----------------------+-----------------------------------------------+---------+----------------+-------------+-----------+---------------------+
| product_id | name                  | description                                   | price   | stock_quantity | category_id | vendor_id | created_at          |
+------------+-----------------------+-----------------------------------------------+---------+----------------+-------------+-----------+---------------------+
|         18 | Gaming Laptop         | High-performance laptop for gaming and work   | 1499.99 |             10 |           1 |         8 | 2025-03-02 18:05:40 |
|         19 | Casual T-Shirt        | 100% Cotton round-neck t-shirt                |   25.99 |             50 |           2 |         5 | 2025-03-02 18:05:40 |
|         20 | Smart Air Conditioner | Energy-efficient 1.5 Ton AC with WiFi control |  599.99 |             15 |           3 |         8 | 2025-03-02 18:05:40 |
|         21 | Machine Learning Book | Advanced guide to Machine Learning and AI     |   39.99 |             30 |           4 |         5 | 2025-03-02 18:05:40 |
|         22 | Home Treadmill        | Automatic treadmill with heart rate monitor   |  799.99 |              5 |           5 |         8 | 2025-03-02 18:05:40 |
+------------+-----------------------+-----------------------------------------------+---------+----------------+-------------+-----------+---------------------+
5 rows in set (0.01 sec)
```
### Users Table
```
mysql> select * from cart;
+---------+---------+------------+----------+
| cart_id | user_id | product_id | quantity |
+---------+---------+------------+----------+
|       1 |       1 |         18 |        2 |
|       2 |       5 |         19 |        1 |
|       3 |       6 |         20 |        3 |
|       4 |       7 |         21 |        1 |
|       5 |       8 |         22 |        2 |
+---------+---------+------------+----------+
5 rows in set (0.01 sec)
```
### Users Table
```
mysql> select * from wishlist;
+-------------+---------+------------+
| wishlist_id | user_id | product_id |
+-------------+---------+------------+
|           6 |       1 |         18 |
|           7 |       5 |         19 |
|           8 |       7 |         20 |
|           9 |       6 |         21 |
|          10 |       8 |         22 |
+-------------+---------+------------+
5 rows in set (0.01 sec)
```
### Users Table
```
mysql> select * from product_variants;
+------------+------------+----------------------+------------------+
| variant_id | product_id | variant_name         | additional_price |
+------------+------------+----------------------+------------------+
|         16 |         18 | 16GB RAM + 512GB SSD |           150.00 |
|         17 |         18 | 32GB RAM + 1TB SSD   |           300.00 |
+------------+------------+----------------------+------------------+
2 rows in set (0.01 sec)
```
### Users Table
```
mysql> select * from orders;
+----------+---------+--------------+--------------+---------------------+
| order_id | user_id | total_amount | order_status | created_at          |
+----------+---------+--------------+--------------+---------------------+
|        1 |       1 |      1350.00 | pending      | 2025-03-02 18:32:33 |
|        2 |       7 |        40.00 | shipped      | 2025-03-02 18:32:33 |
|        3 |       1 |       250.00 | delivered    | 2025-03-02 18:32:33 |
|        4 |       8 |       700.00 | pending      | 2025-03-02 18:32:33 |
|        5 |       5 |      1200.00 | canceled     | 2025-03-02 18:32:33 |
+----------+---------+--------------+--------------+---------------------+
5 rows in set (0.00 sec)
```
### Users Table
```
mysql> select * from order_items;
+---------------+----------+------------+----------+---------+
| order_item_id | order_id | product_id | quantity | price   |
+---------------+----------+------------+----------+---------+
|             1 |        1 |         18 |        2 | 1350.00 |
|             2 |        2 |         19 |        1 |   40.00 |
|             3 |        3 |         20 |        5 |  250.00 |
|             4 |        4 |         21 |        3 |  700.00 |
|             5 |        5 |         22 |        1 | 1200.00 |
+---------------+----------+------------+----------+---------+
5 rows in set (0.00 sec)
```
### Users Table
```
mysql> select * from payments;
+------------+----------+---------+------------------+----------------+----------------+---------+---------------------+
| payment_id | order_id | user_id | payment_method   | transaction_id | payment_status | amount  | created_at          |
+------------+----------+---------+------------------+----------------+----------------+---------+---------------------+
|          1 |        1 |       1 | credit_card      | TXN123456      | completed      | 1350.00 | 2025-03-02 21:04:35 |
|          2 |        2 |       7 | paypal           | TXN789012      | completed      |   40.00 | 2025-03-02 21:04:35 |
|          3 |        3 |       1 | upi              | TXN345678      | pending        |  250.00 | 2025-03-02 21:04:35 |
|          4 |        4 |       8 | debit_card       | TXN901234      | failed         |  700.00 | 2025-03-02 21:04:35 |
|          5 |        5 |       5 | cash_on_delivery | TXN567890      | pending        | 1200.00 | 2025-03-02 21:04:35 |
+------------+----------+---------+------------------+----------------+----------------+---------+---------------------+
5 rows in set (0.00 sec)
```
### Users Table
```
mysql> select * from reviews;
+-----------+---------+------------+--------+----------------------------------------------------------+---------------------+
| review_id | user_id | product_id | rating | review_text                                              | created_at          |
+-----------+---------+------------+--------+----------------------------------------------------------+---------------------+
|        11 |       1 |         18 |      5 | Amazing laptop! Super fast and great battery life.       | 2025-03-02 21:12:49 |
|        12 |       5 |         19 |      4 | Good quality t-shirt, but size runs a bit small.         | 2025-03-02 21:12:49 |
|        13 |       7 |         20 |      3 | Decent fridge, but makes some noise.                     | 2025-03-02 21:12:49 |
|        14 |       4 |         21 |      5 | Excellent book, very informative and well-written.       | 2025-03-02 21:12:49 |
|        15 |       6 |         22 |      2 | The football is okay, but the stitching could be better. | 2025-03-02 21:12:49 |
+-----------+---------+------------+--------+----------------------------------------------------------+---------------------+
5 rows in set (0.01 sec)
```
### Users Table
```
mysql> select * from shipping;
+-------------+----------+-----------------+-----------------+--------------------+
| shipping_id | order_id | tracking_number | shipping_status | estimated_delivery |
+-------------+----------+-----------------+-----------------+--------------------+
|           6 |        1 | TRK1234567890   | shipped         | 2025-03-10         |
|           7 |        2 | TRK9876543210   | processing      | 2025-03-12         |
|           8 |        3 | TRK5678901234   | delivered       | 2025-03-05         |
|           9 |        4 | TRK4321098765   | shipped         | 2025-03-11         |
|          10 |        5 | TRK2468135790   | processing      | 2025-03-13         |
+-------------+----------+-----------------+-----------------+--------------------+
5 rows in set (0.01 sec)
```
### Users Table
```
mysql> select * from live_chat;
+---------+-----------+-------------+-------------------------------------------------+---------------------+
| chat_id | sender_id | receiver_id | message                                         | sent_at             |
+---------+-----------+-------------+-------------------------------------------------+---------------------+
|       1 |         1 |           5 | Hello Alice! I have a question about a product. | 2025-03-02 21:48:10 |
|       2 |         5 |           4 | Sure! How can I help you?                       | 2025-03-02 21:48:10 |
|       3 |         6 |           5 | David, please update your vendor profile.       | 2025-03-02 21:48:10 |
|       4 |         5 |           6 | Okay, I will update it soon.                    | 2025-03-02 21:48:10 |
|       5 |         1 |           4 | Hey John, did you receive your order?           | 2025-03-02 21:48:10 |
+---------+-----------+-------------+-------------------------------------------------+---------------------+
5 rows in set (0.01 sec)
```
### Users Table
```
mysql> select * from categories;
+-------------+------------------+
| category_id | category_name    |
+-------------+------------------+
|           4 | Books            |
|           2 | Clothing         |
|           1 | Electronics      |
|           3 | Home Appliances  |
|           5 | Sports & Fitness |
+-------------+------------------+
5 rows in set (0.00 sec)
```
