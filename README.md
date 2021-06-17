# CS:APP Docker and Materials

CS:APP is an excellent material for learning computer systems and systems programming. However, it is inconvenient to use a virtual machine for self-learners. 
In this repo, I build a Docker image with most pre-requistes installed and attached all lab materials in it.
You can directly use this Docker image: [ccr.ccs.tencentyun.com/apartsa/csapp](ccr.ccs.tencentyun.com/apartsa/csapp) or Docker Hub Link: [xieguochao/csapp](https://hub.docker.com/r/xieguochao/csapp).

The Docker image is still under construction. You are welcome to contribute by adding dependencies to our Dockerfile.

The original materials of CS:APP is from CMU: [CS:APP labs](http://csapp.cs.cmu.edu/3e/labs.html). 

The code server is based on [https://github.com/cdr/code-server](https://github.com/cdr/code-server).

## Manual

A docker environment is required. You can Google and install Docker.

To run it, first clone the repo: `git clone github.com/XieGuochao/csapp`.

Change directory: `cd csapp`.

Make the folder `labs` accessable by our container: `sudo chmod a+rwx -R ./labs`.

Then, run `docker run -p 7777:7777 -v "$PWD/labs:/home/csapp/project" csapp`, which will sync your lab codes with the Code Server. You can find all files in `labs` under `/home/csapp/project`.

You can access your labs via browser [http://localhost:7777/](http://localhost:7777/) with password `csapp`.
