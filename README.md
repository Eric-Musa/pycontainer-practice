# pycontainer-practice
Practicing containerizing Python applications with Docker or Podman.\
### NOTE, this requires `podman` or `docker` (I used `podman`)
#### Follow the installation instructions for `podman` here first (https://podman.io/getting-started/installation)\
## TO RUN THIS FROM SCRATCH:
1. `podman build -t pycontainer pycontainer`
2. `podman run -d -p 5059:5050 pycontainer`
3. go to https://localhost:5059