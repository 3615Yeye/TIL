# SQL query directly in CLI
mysql -u user -p dbname -e "SELECT * FROM some WHERE beyond = the sea" > results.txt

# SQL query in a file
mysql -u user -p dbname < query.sql > results.txt
