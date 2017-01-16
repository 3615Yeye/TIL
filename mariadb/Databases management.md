# Create database
CREATE DATABASE dbname;

## With UTF-8 charset
Best practice  (source : http://stackoverflow.com/questions/766809/whats-the-difference-between-utf8-general-ci-and-utf8-unicode-ci): 
CREATE DATABASE dbname CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

Old way :
CREATE DATABASE mydatabase CHARACTER SET utf8 COLLATE utf8_general_ci;

# Delete database
DROP DATABASE dbname;

# Dump database
mysqldump -u user -p dbname > dbnameDump_Date.sql
