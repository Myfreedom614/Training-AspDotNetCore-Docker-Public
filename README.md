## Lab
1. [VisualStudio + 本地 + Docker + ASP.NET](https://github.com/wu-wenxiang/Training-AspDotNetCore-Docker-Public/tree/master/Docker-AspDotNet)
1. [VisualStudio + 本地 + Docker + ASP.NET Core](https://github.com/wu-wenxiang/Training-AspDotNetCore-Docker-Public/tree/master/Docker-AspDotNetCore)
1. [VisualStudio + Publish + Server2016 + Docker + ASP.NET Core](https://github.com/aspnet/Tooling/blob/AspNetVMs/docs/create-asp-net-vm-with-webdeploy.md): 
	- VS Deployment: Azure VM Instance
1. VisualStudio + Publish + CentOS + Docker + ASP.NET Core
	- VS Deployment: Container Registry: Docker Hub
	- Publish
	- Then on CentOS, pull: `sudo docker pull maodouzi/aspdotnetcorewebapi:20180604014902`, not latest
	- Then run: `sudo docker run -p 8080:80 maodouzi/aspdotnetcorewebapi:20180604014902`, remember open 8080 ACL in Azure portal.
1. VScode + 本地 + Docker + ASP.NET Core
1. VScode + Publish + Docker + ASP.NET Core
1. VScode + Debug + Docker + ASP.NET Core 
1. Server2016 + Docker + ASP.NET Core
1. CentOS + Docker + ASP.NET Core