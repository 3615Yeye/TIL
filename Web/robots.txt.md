# Directory
The robots.txt must be accessible at the root of the domaine name like : www.yourdomain.com/robots.txt.

# Development evironment good practice
The development environment should not be indexed by robots :
User-agent: *
Disallow: /

# Exclude paths
Disallow: /path/to/exlude/

# Add exception
Allow: /path/to/exlude/but/not/this/one/
