# Create a named container from image
docker run -d --name="container_name" imageGroupe/imageName:version

# Expose a container port (-p host_port:container_port)
docker run -tid -p 80:80 --name container_name 

# Map a host directory to a container directory (-v host_path:container_path)
docker run -tid -p 80:80 --name container_name -v host_path:container_path

## If you encounter a SELinux issue you can use this workaround
chcon -Rt svirt_sandbox_file_t host_path

# Exec a command (like bash) in a container
docker exec -it container_name command
