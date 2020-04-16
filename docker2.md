# TASK1
Write python/shell script to launch 100 containers that keeps running even after reboot
Answer:
#Bash script
count=1
while [ $count -le 100 ]
do
  if [ $count -lt 26 ]
  then
    sudo docker container run -d --restart unless-stopped --name adhocnw$count alpine 
  elif [[ ($count -ge 26) && ($count -le 50) ]]
  then
    sudo docker container run -d --restart unless-stopped --name adhocnw$count fedora 
  elif [[ ($count -ge 51) && ($count -le 75) ]]
  then
    sudo docker container run -d --restart unless-stopped --name adhocnw$count centos 
  else [[ ($count -ge 76) && ($count -le 100) ]]
    sudo docker container run -d --restart unless-stopped --name adhocnw$count java 
  fi
  ((count++))
done

# TASK2
Write a combination of Docker and OS commands to get list of Name and Creation time of all containers and store them in a list
Answer:
docker ps -a --format "table {{.ContainerName}}\t{{.Time}}" > yo.txt
cat yo.txt

# TASK3
Creating a container from custom docker image with parent process as firefox.
Answer
 #I dont have docker installed locally in my system 
 
# TASK4
 Get the RAM & CPU consumption from 100 containers of task 1 and store in text file
 Answer
 docker stats --all --no-stream --format "table {{.ContainerName}}\t{{.CPU}}\t{{.RAMUsage}}" > yoo.txt
 cat yoo.txt
