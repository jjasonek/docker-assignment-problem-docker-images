## FIRST RUN
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker run -it --rm 15e5614526a9
(1) Metric (m, kg) or (2) Non-Metric (ft, pounds)?
Please choose: 1
Please enter your height in meters
Your height: 1.62
Please enter your weight in kilograms
Your weight: 75
Your body-mass-index: 28.577960676726104
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED        STATUS        PORTS                  NAMES
a361322f5f86   a62b6d2f1f1a   "docker-entrypoint.s…"   21 hours ago   Up 21 hours   0.0.0.0:3000->80/tcp   my_container_name



## USING CONTAINER NAME
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker run -it --name bmi_counter 15e5614526a9
(1) Metric (m, kg) or (2) Non-Metric (ft, pounds)?
Please choose: 1
Please enter your height in meters
Your height: 1.62
Please enter your weight in kilograms
Your weight: 78
Your body-mass-index: 29.721079103795148
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS                      PORTS                  NAMES
e20f463a7a59   15e5614526a9   "python3 bmi.py"         23 seconds ago   Exited (0) 12 seconds ago                          bmi_counter
a361322f5f86   a62b6d2f1f1a   "docker-entrypoint.s…"   21 hours ago     Up 21 hours                 0.0.0.0:3000->80/tcp   my_container_name
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker stop bmi_counter
bmi_counter

PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker start -ai bmi_counter
(1) Metric (m, kg) or (2) Non-Metric (ft, pounds)?
Please choose: 1
Please enter your height in meters
Your height: 1.62
Please enter your weight in kilograms
Your weight: 78
Your body-mass-index: 29.721079103795148
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker stop bmi_counter
bmi_counter
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app> docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS                      PORTS                  NAMES
e20f463a7a59   15e5614526a9   "python3 bmi.py"         4 minutes ago   Exited (0) 22 seconds ago                          bmi_counter
a361322f5f86   a62b6d2f1f1a   "docker-entrypoint.s…"   21 hours ago    Up 21 hours                 0.0.0.0:3000->80/tcp   my_container_name
PS C:\Training\Docker\assignment-problem-docker-images\assignment-problem\node-app>