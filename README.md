# pycontainer-practice
Practicing containerizing Python applications with Docker or Podman.

TO RUN THIS FROM SCRATCH:
1. `podman build -t pycontainer pycontainer`
2. `podman run -d -p 5059:5050 pycontainer`
3. go to https://localhost:5059