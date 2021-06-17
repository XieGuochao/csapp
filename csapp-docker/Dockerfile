FROM ubuntu:20.04
ARG arch_name=amd64

RUN cp /etc/apt/sources.list /etc/apt/sources.backup.list

# Please comment this line if you are not using Tencent Cloud network
# COPY sources.list /etc/apt/sources.list

RUN apt-get update
RUN apt-get install -y cmake gdb python python3 vim emacs locales
RUN apt-get install -y curl sudo
RUN useradd -m csapp && \
    echo "root ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers && \
    echo "csapp ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers 
RUN locale-gen en_US.UTF-8

ENV LANG=en_US.utf8 \
    LANGUAGE=en_US.UTF-8 \
    LC_ALL=en_US.UTF-8

# Network Packages
RUN apt-get install -y aria2
RUN aria2c https://github.com.cnpmjs.org/cdr/code-server/releases/download/v3.10.2/code-server_3.10.2_${arch_name}.deb && \
    dpkg -i code-server_3.10.2_${arch_name}.deb

RUN apt-get install -y net-tools
RUN usermod -s /bin/bash csapp
RUN chsh -s /bin/bash csapp
ENV SHELL=/bin/bash 

RUN apt-get install -y cgdb git

# DataLab
RUN if [ "${arch_name}" = "arm64" ] ; then apt-get install -y g++-multilib-arm-linux-gnueabi; else apt-get install -y g++-multilib; fi

# ArchLab
RUN apt-get install -y flex bison libgetopt-complete-perl

# CacheLab
RUN apt-get install -y valgrind

USER csapp

# Office Viewer Extension
RUN mkdir /home/csapp/extensions
ADD cweijan.vscode-office-2.0.3.vsix /home/csapp/extensions
RUN code-server --install-extension /home/csapp/extensions/cweijan.vscode-office-2.0.3.vsix

# Cpp Extension
ADD cpptools-linux.vsix /home/csapp/extensions
RUN code-server --install-extension /home/csapp/extensions/cpptools-linux.vsix
# RUN code-server --install-extension ms-vscode.cpptools

# Formatter Extension
RUN code-server --install-extension esbenp.prettier-vscode

# Markdown Extension
RUN code-server --install-extension yzhang.markdown-all-in-one

# Material Theme Extension
RUN code-server --install-extension equinusocio.vsc-material-theme 

USER root

# Python3-pip
RUN apt-get update
RUN apt-get install -y python3-dev python3-pip python3-setuptools

# Fuck Extension
RUN pip3 install thefuck
RUN echo "eval \"\$(thefuck --alias)\" " >> /home/csapp/.bashrc

RUN chown csapp -R /home/csapp/.local/share/

RUN cp /etc/apt/sources.list /etc/apt/sources-tencent.list
RUN mv /etc/apt/sources.backup.list /etc/apt/sources.list
RUN apt-get update

EXPOSE 7777

ENV PASSWORD=csapp

USER csapp


CMD [ "code-server", "--bind-addr", "0.0.0.0:7777", "--auth", "password" ]
