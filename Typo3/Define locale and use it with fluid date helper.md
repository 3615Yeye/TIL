# Check on the server the available locale
locale -a

# Update the typoscript configuration with the choosen locale
config.locale_all = fr_FR

# Use fluid helper with % in the format to use strftime which support locales instead of date() who doesn't
# Date formats available : http://php.net/manual/en/function.strftime.php
<f:format.date format="%e %A">{dateObject}</f:format.date>
