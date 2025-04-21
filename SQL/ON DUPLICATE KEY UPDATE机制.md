```
INSERT INTO users (id, username, email, name)
VALUES (1, 'john_doe', 'john@example.com', 'John Doe')
ON DUPLICATE KEY UPDATE
    username = VALUES(username),
    email = VALUES(email),
    name = VALUES(name);
```
### 
如果表中已经存在 id = 1 的记录，那么 id 是主键，会首先触发主键冲突。此时，数据库会执行更新操作，更新 id = 1 的记录，将 username、email 和 name 设置为新值。
如果表中没有 id = 1 的记录，但存在 username = 'john_doe' 的记录，那么 username 是唯一键，会触发唯一键冲突。此时，数据库会执行更新操作，更新 username = 'john_doe' 的记录。
如果同时存在 id = 1 和 username = 'john_doe' 的记录，那么主键冲突会被优先检测到，数据库会根据主键冲突来执行更新。
