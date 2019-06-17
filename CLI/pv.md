# pv (Pipe Viewer)
Display the progression and ETA when piping data.

Example when used importing a mysql dump of 2.4GB :

``` bash
pv mysqldump.sql | mysql -u user -p dbname
```

 562MiO 0:04:38 [1,27MiB/s] [============>                                ] 22% ETA 0:15:33
