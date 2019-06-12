# How to properly start a bash script

``` bash
#!/usr/bin/env bash

set -o errexit
set -o nounset
set -o pipefail
```

The first line is thought for UNIX like portability.

The second line tell bash to stop the script if an error occur. 

The third line tell bash to stop if an unset variable is called during the script execution.

The last line tell bash to get errors when chaining programs (eg. catch a mysqldump error on thius command : mysqldump | gzip).
