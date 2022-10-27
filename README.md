
# OPT INDUSTRIES

Github Repo for coding challenge of OPT Industries




## Authors

- [@krunalna](https://www.github.com/krunalna)



## Installation

Clone this repository by using below command

```bash
   git clone https://github.com/krunalna/OPT_INDUSTRIES.git
```

Go to your the location and run the following command. 
Please Note: It is assumed that you have already installed docker. If not please refer official documentation

```bash

    docker import krunal_code.tar <your_name>:latest
    docker images
    docker run -t <your_name>:latest bash
```

Replace <your_name> with any name variable name you want.

Open a new terminal to get the container_id.
You'll need to get the container id  of the docker image you just ran by using the following command.

```bash

    docker ps -a
```

After getting the container ID, store it in a ENV variable by using the following command

```bash

    export CID = <container_id>
```

Replace <container_id> with the id that you just copied.

Now, we are done with setting up the docker container. We can proceed with running our actual code.

Important point to remember: Each time you open a new terminal, you'll have to run the following command first.
Lets call this command as MAIN command.
``` bash
    docker exec -it $CID bash

```

Once you have executed the above command, you open a new terminal in the docker environment. You can verfiy
this by checking the username in the terminal. It should be similar to root@<container_id>


Here comes the execution of the challenge.

In the first termianal, runn the MAIN command and then run the following command

```bash
    cd root && python3 server.py
```

This command will change the directory to root and run the server.py file. Server.py file is the Flask App incrementer file.
You can keep this terminal open


Now, open a second terminal and execute the MAIN command first

``` bash

    cd root/catkin_ws && source /opt/ros/noetic/setup.bash && source devel/setup.bash && roscore

```

This commands sources the ROS environments and starts the roscore. Keep this terminal open as well.

Lastly, Open a third terminal and execute the MAIN Command first.

``` bash
    d root/catkin_ws && source /opt/ros/noetic/setup.bash && source devel/setup.bash && rosrun OPT_INDUSTRIES talker.py
```

You should now see an incrementing integer displayed on the terminal. This incrementing integer is fetched from the Flask app that is running 
in the terminal 1.








## References:

https://wiki.ros.org/ROS/Tutorials/WritingPublisherSubscriber%28python%29

https://www.digitalocean.com/community/tutorials/how-to-make-a-web-application-using-flask-in-python-3
