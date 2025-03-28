FROM fedora:41
RUN yum update -y && yum install wget -y
WORKDIR /tmp
RUN wget https://github.com/containerd/containerd/releases/download/v1.6.6/containerd-1.6.6-linux-amd64.tar.gz && tar Czxvf /usr/local containerd-1.6.6-linux-amd64.tar.gz
RUN modprobe -a overlay || true
RUN lsmod | grep overlay
RUN mkdir -p /etc/containerd/
RUN containerd config default | tee /etc/containerd/config.toml
RUN wget https://github.com/opencontainers/runc/releases/download/v1.1.3/runc.amd64 && sudo install -m 755 runc.amd64 /usr/local/sbin/runc
RUN dnf -y install dnf-plugins-core && wget https://download.docker.com/linux/fedora/docker-ce.repo
RUN dnf config-manager addrepo --from-repofile=docker-ce.repo 
# using nerdctl to test the containerd environment
RUN wget https://github.com/containerd/nerdctl/releases/download/v0.21.0/nerdctl-0.21.0-linux-amd64.tar.gz
RUN sudo tar Cxzvf /usr/local/bin nerdctl-0.21.0-linux-amd64.tar.gz
ENTRYPOINT /bin/sh
# to get the ip address of the machine
# need to check in /var/run that the socket is alive /var/run/containerd/containerd.sock	
#tail -1 hosts | awk '{print $1}'
# if we start the service manually we should add a restart module
#ExecStartPre=-/sbin/modprobe overlay
#ExecStart=/usr/local/bin/containerd


