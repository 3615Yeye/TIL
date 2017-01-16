# Database

## Regular

### Export
mysqldump -u user -p dbname > dbname_`date -I`.sql

### Import
cat dbname_date.sql.gz | mysql -u {user} -p {database}

## Compressed

### Export
mysqldump -u user -p dbname | gzip > dbname_`date -I`.sql.gz

### Import
gzip -dc < dbname_date.sql.gz | mysql -u {user} -p {database}

# Table

# Dump
mysqldump -u user -p dbname tablename > dbname_tablename_`date -I`.sql

## Compressed dump
mysqldump -u user -p dbname tablename | gzip > dbname_tablename_`date -I`.sql.gz
