# Database

## Regular

### Export
mysqldump -u user -p dbname > dbname_`date +"%Y-%m-%d-%Hh%m`.sql

### Import
cat dbname_date.sql.gz | mysql -u {user} -p {database}

## Compressed

### Export
mysqldump -u user -p dbname | gzip > dbname_`date +"%Y-%m-%d-%Hh%m`.sql.gz

### Import
gzip -dc < dbname_date.sql.gz | mysql -u {user} -p {database}

# Table

## Dump
mysqldump -u user -p dbname tablename > dbname_tablename_`date +"%Y-%m-%d-%Hh%m`.sql

### Compressed dump
mysqldump -u user -p dbname tablename | gzip > dbname_tablename_`date +"%Y-%m-%d-%Hh%m`.sql.gz

## CSV dump with ; separator and without the FILE grant
mysql -u user -p dbname -e 'SELECT * FROM mytable' | sed "s/'/\'/;s/\t/\"\;\"/g;s/^/\"/;s/$/\"/;s/\n//g" > mytable.`date +"%Y-%m-%d-%Hh%m`.csv

## Tricky CSV import with ; separator and without the FILE grant (definitely messy but might be usefull)
mysqldump -u user -p dbname tablename | gzip > dbname_tablename_`date +"%Y-%m-%d-%Hh%m`.sql.gz

Optionnaly remove fields from the CSV.

Replace the INSERT INTO statements with :
INSERT INTO mytable (comma separated remaining columns in the CSV)
VALUES
paste the CSV here and for each lines do (vim macros are your friend) :
    replace ; with ","
    Wrap the line with (" | "),
    Replace ), with ); for the last line

Import the created CSV file
$$$
