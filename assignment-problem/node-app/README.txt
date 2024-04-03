## FIRST RUN
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker run -p 3001:3000 -d --rm 8d911866707e
ba2698d2b32f8aa5c466b7de41755c107fce8b082ee9eb0c80dba8c214705a69
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                            NAMES
ba2698d2b32f   8d911866707e   "docker-entrypoint.s…"   28 seconds ago   Up 27 seconds   80/tcp, 0.0.0.0:3001->3000/tcp   admiring_wozniak
a361322f5f86   a62b6d2f1f1a   "docker-entrypoint.s…"   21 hours ago     Up 21 hours     0.0.0.0:3000->80/tcp             my_container_name
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker stop admiring_wozniak



## USING NAMES
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker run -p 3001:3000 -d --name hello_node 8d911866707e
3986fb8777488f0e244955dec0586b6f799c394dfa843dc22ee1da3bc4fad255
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker stop hello_node
hello_node
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED              STATUS                            PORTS                  NAMES
3986fb877748   8d911866707e   "docker-entrypoint.s…"   About a minute ago   Exited (137) About a minute ago                          hello_node
e20f463a7a59   15e5614526a9   "python3 bmi.py"         10 minutes ago       Exited (0) 6 minutes ago                                 bmi_counter
a361322f5f86   a62b6d2f1f1a   "docker-entrypoint.s…"   22 hours ago         Up 22 hours                       0.0.0.0:3000->80/tcp   my_container_name

PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker start hello_node
hello_node
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS          PORTS                            NAMES
3986fb877748   8d911866707e   "docker-entrypoint.s…"   3 minutes ago   Up 23 seconds   80/tcp, 0.0.0.0:3001->3000/tcp   hello_node
a361322f5f86   a62b6d2f1f1a   "docker-entrypoint.s…"   22 hours ago    Up 22 hours     0.0.0.0:3000->80/tcp             my_container_name
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker stop hello_node
hello_node
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app>


## CLEAN UP
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker images
REPOSITORY         TAG                  IMAGE ID       CREATED             SIZE
<none>             <none>               15e5614526a9   About an hour ago   130MB
<none>             <none>               8d911866707e   About an hour ago   212MB
my_tag             latest               e197ccb2bed1   21 hours ago        1.11GB
<none>             <none>               a62b6d2f1f1a   22 hours ago        1.11GB
<none>             <none>               34d52ade3c61   4 days ago          1.02GB
node               latest               c3978d05bc68   3 weeks ago         1.1GB
local/apache-php   5                    35dd64e3e7cc   23 months ago       44.5MB
local/apache-php   7                    a1524730afe0   23 months ago       21.2MB
local              fromscratch          954bd8778be6   23 months ago       5.59MB
local              dockerfile-example   0224f749c762   23 months ago       7.17MB
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS                        PORTS                  NAMES
3986fb877748   8d911866707e   "docker-entrypoint.s…"   17 minutes ago   Exited (137) 13 minutes ago                          hello_node
e20f463a7a59   15e5614526a9   "python3 bmi.py"         26 minutes ago   Exited (0) 22 minutes ago                            bmi_counter
a361322f5f86   a62b6d2f1f1a   "docker-entrypoint.s…"   22 hours ago     Up 22 hours                   0.0.0.0:3000->80/tcp   my_container_name
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker rm hello_node bmi_counter
hello_node
bmi_counter
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker rmi 15e5614526a9 8d911866707e
Deleted: sha256:15e5614526a97c70f58e8a90be778f0da9ede87de975e14f16a84c9b32937081
Deleted: sha256:8d911866707eb3ca04b3a1cb59bfbc15d70bfed0d3c9048bfe1d1936a825972f


## IMAGE NAMES
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker build . -t hello_node:slim
[+] Building 6.0s (9/9) FINISHED                                                                                                                                                                                     docker:default
 => [internal] load build definition from Dockerfile                                                                                                                                                                           0.0s
 => => transferring dockerfile: 135B                                                                                                                                                                                           0.0s
 => [internal] load metadata for docker.io/library/node:slim                                                                                                                                                                   1.0s
 => [internal] load .dockerignore                                                                                                                                                                                              0.0s
 => => transferring context: 2B                                                                                                                                                                                                0.0s
 => [1/4] FROM docker.io/library/node:slim@sha256:ab9d8781cb3fe8b6429d68c6ce19512a4ff526a6688240249ca15069b8124626                                                                                                             0.0s
 => [internal] load build context                                                                                                                                                                                              0.0s
 => => transferring context: 4.98kB                                                                                                                                                                                            0.0s
 => CACHED [2/4] WORKDIR /app                                                                                                                                                                                                  0.0s
 => [3/4] COPY . /app                                                                                                                                                                                                          0.0s
 => [4/4] RUN npm install                                                                                                                                                                                                      4.7s
 => exporting to image                                                                                                                                                                                                         0.1s
 => => exporting layers                                                                                                                                                                                                        0.1s
 => => writing image sha256:5f123a3e6bcb96832e42195a0233cb7e36b5fd5bbda51a1b92c531b32656f5d3                                                                                                                                   0.0s
 => => naming to docker.io/library/hello_node:slim                                                                                                                                                                             0.0s

What's Next?
  1. Sign in to your Docker account → docker login
  2. View a summary of image vulnerabilities and recommendations → docker scout quickview
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker images
REPOSITORY         TAG                  IMAGE ID       CREATED          SIZE
hello_node         slim                 5f123a3e6bcb   13 seconds ago   212MB
