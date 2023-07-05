# CS:APP Docker and Materials

CS:APP is an excellent material for learning computer systems and systems programming. However, it is inconvenient to use a virtual machine for self-learners. 
In this repo, I build a Docker image with most pre-requistes installed and attached all lab materials in it.
You can directly use this Docker image [xieguochao/csapp](https://hub.docker.com/r/xieguochao/csapp).

The original materials of CS:APP is from CMU: [CS:APP labs](http://csapp.cs.cmu.edu/3e/labs.html). 

The code server is based on [https://github.com/cdr/code-server](https://github.com/cdr/code-server).

## How to Use It?

### Install Docker or Podman

- [Docker Engine](https://docs.docker.com/engine/install/)
- [Podman](https://podman.io/docs/installation)

### Clone Repository

1. `git clone --branch 1.8 https://github.com/XieGuochao/csapp.git`.
2. `cd csapp`.

### Build Image (Optional)

1. `cd csapp-docker`
2. `docker build -t csapp .`.

### Run

Under the root directory.

`docker run -p 7777:7777 -v "$PWD/labs:/home/csapp/project" csapp`

Then you can access your labs via browser [http://localhost:7777/](http://localhost:7777/) with password `csapp`. You can find all files in `labs` under `/home/csapp/project`.

## Troubleshootings

You can raise an issue and we will help you.
