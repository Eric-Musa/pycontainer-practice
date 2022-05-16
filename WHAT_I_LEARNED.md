# What I Learned

Ports are annoying
The port that the flask app runs on inside the container:
```
if __name__ == "__main__":
    app.run(debug=True, host='0.0.0.0', port=5050)
```
(the 5050 above) is the port running IN THE CONTAINER.
The host IP address (the '0.0.0.0' above) does not depend solely on the container.
BUT the container has to publish Flask's port (5050) in order for the host to be able to serve the app.
*NOTE using the `EXPOSE` argument to expose a port in the `Dockerfile` only enables the port to be access from other containers, not externally.

The command `docker run -p <host_port>:<container_port> imageName` sums up the necessary step to expose the Flask port.


## Popular commands:
 - `podman build -t pycontainer pycontainer` --> builds the pycontainer image
 - `sudo lsof -i tcp:5050` --> prints processes currently using the TCP 5050 port
 - `podman pd -a` --> list all podman containers
 - `podman ps -a | awk 'NR>1 {print $1}'` --> pipe podman containers to awk and only print out the PIDs
 - `podman ps -a | awk 'NR==2 {print $1}'` --> pipe podman containers to awk and only print out the PID of the first process (header line NR==1)
 - `podman ps -a | awk 'NR>1 {print $1 $2}'` --> pipe podman containers to awk and print out the PIDs and Names
 - `podman stop $(podman ps -a | awk 'NR>1 {print $1}')` --> stop all running podman containers
 - `podman container prune` --> removes all stopped containers from storage
 - `podman run -d -p 5059:5050 pycontainer` --> run the pycontainer image (running on container port 5050) and publish it to host (0.0.0.0, specified in app.py) port 5059