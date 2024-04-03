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