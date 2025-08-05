1. List all Docker networks

bash
Copy
Edit
docker network ls
This command lists all existing Docker networks, including the default ones like bridge, host, and none.

2. Inspect a specific network

php-template
Copy
Edit
docker network inspect <network-name>
Example:

nginx
Copy
Edit
docker network inspect bridge
This shows details like connected containers, subnet, gateway, and IP addresses.

3. Create a custom bridge network

pgsql
Copy
Edit
docker network create <network-name>
Example:

lua
Copy
Edit
docker network create my-custom-net
Creates a new isolated user-defined bridge network.

4. Remove a Docker network

bash
Copy
Edit
docker network rm <network-name>
Example:

bash
Copy
Edit
docker network rm my-custom-net
This deletes the specified network. You cannot remove a network that has active containers.

5. Connect a running container to a network

pgsql
Copy
Edit
docker network connect <network-name> <container-name>
Example:

perl
Copy
Edit
docker network connect my-custom-net my-nginx
Allows a container to join another network.

6. Disconnect a container from a network

php-template
Copy
Edit
docker network disconnect <network-name> <container-name>
Example:

perl
Copy
Edit
docker network disconnect my-custom-net my-nginx
Removes the container from the specified network.

7. Create a network with a specific driver

lua
Copy
Edit
docker network create --driver bridge my-bridge-net
docker network create --driver overlay my-overlay-net
bridge is used for standalone containers on a single host.
overlay is used in Docker Swarm for multi-host networking.

8. Create a network with a specific subnet and gateway

lua
Copy
Edit
docker network create \
  --subnet=192.168.100.0/24 \
  --gateway=192.168.100.1 \
  my-custom-subnet
This gives you control over the network’s IP range and gateway.

Real-Time Use Case Example: App and DB on same network

css
Copy
Edit
docker network create app-net

docker run -d --name db --network app-net mysql

docker run -d --name app --network app-net myapp
Now the app container can connect to the db container using the name db.

