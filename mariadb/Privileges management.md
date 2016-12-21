# Grant privileges
## Open bar
### All databases
GRANT ALL PRIVILEGES ON *.* TO 'user'@'localhost';

### Specific database
GRANT ALL PRIVILEGES ON dbname.* TO 'user'@'localhost';

### Specific table
GRANT ALL PRIVILEGES ON dbname.table TO 'user'@'localhost';

## Fine-grained
Common privileges : ALL PRIVILEGES, CREATE, DROP, DELETE, INSERT, SELECT, UPDATE

Syntax example :
GRANT SELECT, INSERT, DELETE ON dbname.* TO 'user'@'localhost';

# Apply privileges
FLUSH PRIVILEGES;
