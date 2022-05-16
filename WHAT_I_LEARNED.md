# What I Learned

Ports are annoying
The port that the flask app runs on internally:
```
if __name__ == "__main__":
    app.run(debug=True, host='0.0.0.0', port=5050)
```
(the 5050 above) is the port running IN THE CONTAINER.
The host IP address (the '0.0.0.0' above) does not depend solely on the container.
BUT the container has to expose Flask's port (5050) in order for the host to be able to serve the app.

The command `docker run -p <host_port>:<container_port> imageName` sums up the necessary step to expose the Flask port.