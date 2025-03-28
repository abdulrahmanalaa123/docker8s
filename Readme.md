# docker8s
- Simulating and configuring a k8s cluster on docker

## Building 
- following the build steps at [containerd docs](https://github.com/containerd/containerd/blob/master/BUILDING.md#via-docker-container) into a dockerfile

- installing the image for base containerd supported containerd with seccomp and without 
```
cd containerd
docker build --ssh default=~/.ssh/your_github_ssh -t contd .
```
- to install with seccomp enabled simply uncommend the two lines
```
#RUN apt-get update && \
#    apt-get install -y libseccomp-dev
```
