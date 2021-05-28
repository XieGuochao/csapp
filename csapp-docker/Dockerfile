FROM ubuntu:20.04

COPY sources.list /etc/apt/sources.list

RUN apt-get update
RUN apt-get install -y cmake gdb python python3 vim emacs locales
RUN apt-get install -y curl
RUN useradd -m csapp && \
    echo "root ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers && \
    echo "csapp ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers 
RUN locale-gen en_US.UTF-8

ENV LANG=en_US.utf8 \
    LANGUAGE=en_US.UTF-8 \
    LC_ALL=en_US.UTF-8

RUN curl -fOL github.com.cnpmjs.org/cdr/code-server/releases/download/v3.6.0/code-server_3.6.0_amd64.deb && \
    dpkg -i code-server_3.6.0_amd64.deb

RUN apt-get install -y net-tools

EXPOSE 7777

ENV PASSWORD=csapp

USER csapp

CMD [ "code-server", "--bind-addr", "0.0.0.0:7777", "--auth", "password" ]