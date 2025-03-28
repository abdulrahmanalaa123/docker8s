FROM golang 
USER root
RUN mkdir -p /src/containerd
ADD --chown=root:root --chmod=744 git@github.com:containerd/containerd.git /src/containerd/
ADD --chown=root:root --chmod=744 git@github.com:opencontainers/runc.git /src/runc/
WORKDIR /src/containerd
RUN make && make install
WORKDIR /src/runc
#RUN apt-get update && \
#    apt-get install -y libseccomp-dev
RUN make BUILDTAGS="" && make install BUILDTAGS=""
