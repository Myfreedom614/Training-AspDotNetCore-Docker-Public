## Debug
- Test: `http://localhost:5000/api/values`
- Return: `["value1","value2"]`

## Win10 CE
- Host Linux/Windows, [Switch](https://stackoverflow.com/questions/46779911/asp-net-core-docker-build-error), if hang, restart OS to switch
- Diff config

		diff AspDotNetCore-WebApi-Docker-Win/docker-compose.dcproj AspDotNetCore-WebApi-Docker-Linux/docker-compose.dcproj
		5,6c5,6
		<     <DockerTargetOS>Windows</DockerTargetOS>
		<     <ProjectGuid>f78f0786-ccfa-425d-9c56-36fbd0e818d6</ProjectGuid>
		---
		>     <DockerTargetOS>Linux</DockerTargetOS>
		>     <ProjectGuid>8efd9132-c0c0-4d61-8567-f1bb6674f259</ProjectGuid>
		8c8
		<     <DockerServiceUrl>{Scheme}://{ServiceIPAddress}{ServicePort}</DockerServiceUrl>
		---
		>     <DockerServiceUrl>{Scheme}://localhost:{ServicePort}</DockerServiceUrl>
		diff AspDotNetCore-WebApi-Docker-Win/docker-compose.override.yml AspDotNetCore-WebApi-Docker-Linux/docker-compose.override.yml
		9,13d8
		< 
		< networks:
		<   default:
		<     external:
		<       name: nat
		diff AspDotNetCore-WebApi-Docker-Win/docker-compose.yml AspDotNetCore-WebApi-Docker-Linux/docker-compose.yml
		8c8
		<       dockerfile: AspDotNetCore-WebApi\Dockerfile
		---
		>       dockerfile: AspDotNetCore-WebApi/Dockerfile