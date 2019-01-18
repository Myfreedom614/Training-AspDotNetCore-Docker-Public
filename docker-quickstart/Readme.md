- Build

        $ docker build --tag=friendlyhello .

        $ docker image ls
        REPOSITORY            TAG                 IMAGE ID
        friendlyhello         latest              326387cea398
- Run

        docker run -p 4000:80 friendlyhello
        
        $ curl http://localhost:4000
        <h3>Hello World!</h3><b>Hostname:</b> 8fc990912a14<br/><b>Visits:</b> <i>cannot connect to Redis, counter disabled</i>
- Run Daemon & Stop

        $ docker run -d -p 4000:80 friendlyhello

        $ docker container ls
        CONTAINER ID        IMAGE               COMMAND             CREATED
        1fa4ab2cf395        friendlyhello       "python app.py"     28 seconds ago

        $ docker container stop 1fa4ab2cf395
- Debugging
    - `docker run -it -p 80:80 --entrypoint /bin/bash friendlyhello`
    - `docker run -it friendlyhello python`
- Push & Pull
    
        docker login
        docker tag friendlyhello maodouzi/get-started:part2
        docker push maodouzi/get-started:part2
        // pull
        docker run -p 4000:80 maodouzi/get-started:part2
- Service
	- In a distributed application, different pieces of the app are called “services”. 
	- For example, if you imagine a video sharing site, it probably includes a service for storing application data in a database, a service for video transcoding in the background after a user uploads something, a service for the front-end, and so on.
	- Services are really just “containers in production.” A service only runs one image, but it codifies the way that image runs—what ports it should use, how many replicas of the container should run so the service has the capacity it needs, and so on.
	- Scaling a service changes the number of container instances running that piece of software, assigning more computing resources to the service in the process. 
	- Usage

			docker stack ls                                            # List stacks or apps
			docker stack deploy -c <composefile> <appname>  # Run the specified Compose file
			docker service ls                 # List running services associated with an app
			docker service ps <service>                  # List tasks associated with an app
			docker inspect <task or container>                   # Inspect task or container
			docker container ls -q                                      # List container IDs
			docker stack rm <appname>                             # Tear down an application
			docker swarm leave --force      # Take down a single node swarm from the manager
- Docker-Machine Swarm
	- [VMWare Fusion](https://docs.docker.com/machine/drivers/vm-fusion/)
	- Usage
		
			docker-machine create --driver virtualbox myvm1 # Create a VM (Mac, Win7, Linux)
			docker-machine create -d hyperv --hyperv-virtual-switch "myswitch" myvm1 # Win10
			docker-machine env myvm1                # View basic information about your node
			docker-machine ssh myvm1 "docker node ls"         # List the nodes in your swarm
			docker-machine ssh myvm1 "docker node inspect <node ID>"        # Inspect a node
			docker-machine ssh myvm1 "docker swarm join-token -q worker"   # View join token
			docker-machine ssh myvm1   # Open an SSH session with the VM; type "exit" to end
			docker node ls                # View nodes in swarm (while logged on to manager)
			docker-machine ssh myvm2 "docker swarm leave"  # Make the worker leave the swarm
			docker-machine ssh myvm1 "docker swarm leave -f" # Make master leave, kill swarm
			docker-machine ls # list VMs, asterisk shows which VM this shell is talking to
			docker-machine start myvm1            # Start a VM that is currently not running
			docker-machine env myvm1      # show environment variables and command for myvm1
			eval $(docker-machine env myvm1)         # Mac command to connect shell to myvm1
			& "C:\Program Files\Docker\Docker\Resources\bin\docker-machine.exe" env myvm1 | Invoke-Expression   # Windows command to connect shell to myvm1
			docker stack deploy -c <file> <app>  # Deploy an app; command shell must be set to talk to manager (myvm1), uses local Compose file
			docker-machine scp docker-compose.yml myvm1:~ # Copy file to node's home dir (only required if you use ssh to connect to manager and deploy the app)
			docker-machine ssh myvm1 "docker stack deploy -c <file> <app>"   # Deploy an app using ssh (you must have first copied the Compose file to myvm1)
			eval $(docker-machine env -u)     # Disconnect shell from VMs, use native docker
			docker-machine stop $(docker-machine ls -q)               # Stop all running VMs
			docker-machine rm $(docker-machine ls -q) # Delete all VMs and their disk images
	- Operation

			cp ~/Downloads/boot2docker.iso /Users/wuwenxiang/.docker/machine/cache/
			docker-machine create --driver vmwarefusion myvm1
			docker-machine create --driver vmwarefusion myvm2
			docker-machine ssh myvm1 "docker swarm init --advertise-addr 192.168.2.134"
			docker-machine ssh myvm1 "docker swarm join-token manager"
			docker-machine ssh myvm2 "docker swarm join --token SWMTKN-1-0sqqxtnbgjyy3jx6g74lo6jubd1r431c57so1jptjpkxb22myp-3ngl044srdex55wgtp4pd5c86 192.168.2.134:2377"
			docker-machine ssh myvm1 "docker node ls"
			docker-machine ls
			docker-machine ssh myvm2 "docker node ls"
			docker-machine regenerate-certs myvm1
			docker-machine env myvm1
			docker-machine regenerate-certs myvm2
			eval $(docker-machine env myvm1)
			docker stack deploy -c docker-compose.yml getstartedlab
			docker ps
			docker stack ps getstartedlab
			docker ps
- Stack
	- A stack is a group of interrelated services that share dependencies, and can be orchestrated and scaled together. 
	- A single stack is capable of defining and coordinating the functionality of an entire application (though very complex applications may want to use multiple stacks).
	- Usage