FROM ubuntu:24.04

ARG PUBKEY

RUN apt-get update && apt-get install -y openssh-server sudo python3 ca-certificates && rm -rf /var/lib/apt/lists/*

RUN id -u ubuntu >/dev/null 2>&1 || useradd -m -s /bin/bash ubuntu \
  && echo "ubuntu ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/ubuntu \
  && chmod 0440 /etc/sudoers.d/ubuntu

RUN mkdir -p /home/ubuntu/.ssh \
 && echo "$PUBKEY" > /home/ubuntu/.ssh/authorized_keys \
 && chown -R ubuntu:ubuntu /home/ubuntu/.ssh \
 && chmod 700 /home/ubuntu/.ssh \
 && chmod 600 /home/ubuntu/.ssh/authorized_keys \
 && mkdir -p /run/sshd   

EXPOSE 22

CMD ["/usr/sbin/sshd","-D","-e"]
