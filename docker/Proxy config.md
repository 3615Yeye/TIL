# Find the systemd service file 
systemctl status docker

# Edit the service file (path for Fedora 26, pay attention to the UNIX rights of the file to prevent access to your account)
vim /usr/lib/systemd/system/docker.service 
    [Service]
    Environment="HTTP_PROXY=http://proxy.example.com:80/"

# Reload systemd services and restart docker
systemctl daemon-reload
systemctl restart docker

You can now use docker pull
