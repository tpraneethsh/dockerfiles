### CMD

CMD is the instruction which runs the Container

##### RUN vs CMD  
* RUN command will execute at the time of image creation.  
* CMD command will execute at the time of running container.

In this Part we learn  
  * how to a server image called nginx inside an image.  
  * How to run this image.  
  * After running Docker Image, how to go inside of this nginx server and create a html file.  
  * And finally how to access this html file from the browser.

In Terminal  
CMD folder>  
    docker build -t tpraneethsh/cmd:v1 .        (To create Docker image)  
    docker ps --no-trunc  
    docker run -d tpraneethsh/cmd:v1  
    docker ps  
        CONTAINER ID   IMAGE                COMMAND                  CREATED         STATUS       PORTS     NAMES  
        6cdf7de6fc6e   tpraneethsh/cmd:v1   "nginx -g 'daemon of…"   6 seconds ago   Up 5 seconds             vigilant_payne  

If we Forgot to Give port mapping  

Delete container  
first get the container ID and delete  
    docker ps   
    docker rm -f 6cdf7de6fc6e  
To Delete all containers     
    docker ps -a -q (This gives all container ids)  
    docker rm -f "docker ps -a -q"  


run container  
CMD folder>  
    docker images (to get the container id)  
    docker run -d -p 80:80 tpraneethsh/cmd:v1 (run the container)  
    docker ps (to check the runnning container)  
Login to the container  
    docker exec -it 6cdf7de6fc6e bash  
    cd /usr/share/nginx/html  
    echo "hello world" > hello.html  
Open Browser and http://localhost:80/hello.html  
    