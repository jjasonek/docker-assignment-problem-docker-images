## FIRST RUN
docker run -it --rm 15e5614526a9
(1) Metric (m, kg) or (2) Non-Metric (ft, pounds)?
Please choose: 1
Please enter your height in meters
Your height: 1.62
Please enter your weight in kilograms
Your weight: 75
Your body-mass-index: 28.577960676726104
docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED        STATUS        PORTS                  NAMES
a361322f5f86   a62b6d2f1f1a   "docker-entrypoint.s…"   21 hours ago   Up 21 hours   0.0.0.0:3000->80/tcp   my_container_name



## USING CONTAINER NAME
docker run -it --name bmi_counter 15e5614526a9
(1) Metric (m, kg) or (2) Non-Metric (ft, pounds)?
Please choose: 1
Please enter your height in meters
Your height: 1.62
Please enter your weight in kilograms
Your weight: 78
Your body-mass-index: 29.721079103795148
docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS                      PORTS                  NAMES
e20f463a7a59   15e5614526a9   "python3 bmi.py"         23 seconds ago   Exited (0) 12 seconds ago                          bmi_counter
a361322f5f86   a62b6d2f1f1a   "docker-entrypoint.s…"   21 hours ago     Up 21 hours                 0.0.0.0:3000->80/tcp   my_container_name
docker stop bmi_counter
bmi_counter

docker start -ai bmi_counter
(1) Metric (m, kg) or (2) Non-Metric (ft, pounds)?
Please choose: 1
Please enter your height in meters
Your height: 1.62
Please enter your weight in kilograms
Your weight: 78
Your body-mass-index: 29.721079103795148
docker stop bmi_counter
bmi_counter
docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS                      PORTS                  NAMES
e20f463a7a59   15e5614526a9   "python3 bmi.py"         4 minutes ago   Exited (0) 22 seconds ago                          bmi_counter
a361322f5f86   a62b6d2f1f1a   "docker-entrypoint.s…"   21 hours ago    Up 21 hours                 0.0.0.0:3000->80/tcp   my_container_name



## IMAGE NAMES
docker build . -t bmi_counter:3.12-slim
[+] Building 1.1s (8/8) FINISHED                                                                                                                                                                                     docker:default
 => [internal] load build definition from Dockerfile                                                                                                                                                                           0.0s
 => => transferring dockerfile: 112B                                                                                                                                                                                           0.0s
 => [internal] load metadata for docker.io/library/python:3.12-slim                                                                                                                                                            0.9s
 => [internal] load .dockerignore                                                                                                                                                                                              0.0s
 => => transferring context: 2B                                                                                                                                                                                                0.0s
 => [1/3] FROM docker.io/library/python:3.12-slim@sha256:5dc6f84b5e97bfb0c90abfb7c55f3cacc2cb6687c8f920b64a833a2219875997                                                                                                      0.0s
 => [internal] load build context                                                                                                                                                                                              0.0s
 => => transferring context: 2.81kB                                                                                                                                                                                            0.0s
 => CACHED [2/3] WORKDIR /app                                                                                                                                                                                                  0.0s
 => [3/3] COPY . /app                                                                                                                                                                                                          0.0s
 => exporting to image                                                                                                                                                                                                         0.0s
 => => exporting layers                                                                                                                                                                                                        0.0s
 => => writing image sha256:e3c3239bd4fe695e8d1967b862179fd8001676e19acd8c95bed2aa72534df67c                                                                                                                                   0.0s
 => => naming to docker.io/library/bmi_counter:3.12-slim                                                                                                                                                                       0.0s

What's Next?
  1. Sign in to your Docker account → docker login
  2. View a summary of image vulnerabilities and recommendations → docker scout quickview
docker images
REPOSITORY         TAG                  IMAGE ID       CREATED         SIZE
bmi_counter        3.12-slim            e3c3239bd4fe   7 seconds ago   130MB


## RUNNING CONTAINERS BASED ON TAGGED IMAGES
docker run -ti --rm bmi_counter:3.12-slim
(1) Metric (m, kg) or (2) Non-Metric (ft, pounds)?
Please choose: 1
Please enter your height in meters
Your height: 1.62
Please enter your weight in kilograms
Your weight: 78
Your body-mass-index: 29.721079103795148
docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED        STATUS        PORTS                  NAMES
a361322f5f86   a62b6d2f1f1a   "docker-entrypoint.s…"   22 hours ago   Up 22 hours   0.0.0.0:3000->80/tcp   my_container_name
