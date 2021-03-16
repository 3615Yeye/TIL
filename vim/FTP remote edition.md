# Store the connection information in .netrc in HOME
```
vim ~/.netrc
    machine HOSTNAME login USER password PASSWORD
```

```
# Make .netrc readable only by you
chomd 600 ~/.netrc 
```

# Usage
```
# File
vim ftp://HOSTNAME/path/to/file

# Directory (note the ending slash)
vim ftp://HOSTNAME/path/to/dir/
```
