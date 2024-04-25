FROM hashicorp/tfc-agent

USER root

ENV DEBIAN_FRONTEND="noninteractive" 
ENV DEBCONF_NONINTERACTIVE_SEEN=true

# Install Python related libraries
RUN apt-get update && apt-get -y install psmisc;
RUN pip3 install requests pyyaml

# Install the latest version of kubectl
RUN curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl && \
    install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

# Install kubelogin
RUN curl -L -o kubelogin.zip https://github.com/Azure/kubelogin/releases/latest/download/kubelogin-linux-amd64.zip && \
    unzip kubelogin.zip && \
    install -o root -g root -m 0755 ./bin/linux_amd64/kubelogin /usr/local/bin && \
    rm kubelogin.zip


USER tfc-agent
