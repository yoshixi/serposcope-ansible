FROM debian:9.5

RUN apt-get -y update
RUN apt-get -y install curl vim less sudo wget gnupg ssh
RUN apt-get -y install openssh-server openssh-client

RUN echo 'deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main' >> /etc/apt/sources.list
RUN sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
RUN sudo apt update
RUN sudo apt -y install ansible
RUN mkdir /run/sshd

# sshd起動時に公開鍵が必要なため、作成
# RUN if [[ ! -f /etc/ssh/ssh_host_rsa_key ]]; then ssh-keygen -f /etc/ssh/ssh_host_rsa_key -N '' -t rsa; fi
# RUN if [[ ! -f /etc/ssh/ssh_host_rsa_key ]]; then ssh-keygen -f /etc/ssh/ssh_host_ecdsa_key -N '' -t ecdsa; fi

# rootでログインできるようにする
RUN sed -ri 's/^#PermitEmptyPasswords no/PermitEmptyPasswords yes/' /etc/ssh/sshd_config
RUN sed -ri 's/^#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -ri 's/^UsePAM yes/UsePAM no/' /etc/ssh/sshd_config
RUN passwd -d root

EXPOSE 22
EXPOSE 80
EXPOSE 443

COPY . /hoge
CMD ["/usr/sbin/sshd", "-D"]

# CMD ansible-playbook -i /hoge/hosts /hoge/site.yml --connection=local && tail -f /dev/null
