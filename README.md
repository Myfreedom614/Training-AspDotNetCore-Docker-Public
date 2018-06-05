## Lab
1. [VisualStudio + 本地 + Docker + ASP.NET](https://github.com/wu-wenxiang/Training-AspDotNetCore-Docker-Public/tree/master/Docker-AspDotNet)
1. [VisualStudio + 本地 + Docker + ASP.NET Core](https://github.com/wu-wenxiang/Training-AspDotNetCore-Docker-Public/tree/master/Docker-AspDotNetCore)
1. [VisualStudio + Publish + Server2016 + ASP.NET Core](https://github.com/aspnet/Tooling/blob/AspNetVMs/docs/create-asp-net-vm-with-webdeploy.md): 
	- VS Deployment: Azure VM Instance
1. VisualStudio + Publish + CentOS + Docker + ASP.NET Core
	- VS Deployment: Container Registry: Docker Hub
	- Publish
	- Then on CentOS, pull: `sudo docker pull maodouzi/aspdotnetcorewebapi:20180604014902`, not latest
	- Then run: `sudo docker run -p 8080:80 maodouzi/aspdotnetcorewebapi:20180604014902`, remember open 8080 ACL in Azure portal.
1. VisualStudio + RemoteDebug
	- [Attaching to an existing ASP.NET Core process running inside a Windows Docker container](https://github.com/riskfirst/debugging-aspnet-core-windows-docker)
	- [Debugging containerized ASP.NET Core application from VS Code](https://github.com/aspnet/aspnet-docker/issues/186)
	- [How to debug a .NET Core app runnig in Linux Docker container from Visual Studio
](https://stackoverflow.com/questions/48661857/how-to-debug-a-net-core-app-runnig-in-linux-docker-container-from-visual-studio)
	- [What is the story of Performance Counters for .NET Core?](https://stackoverflow.com/questions/38124196/what-is-the-story-of-performance-counters-for-net-core)
	- [Docker打包 Asp.Net Core应用，在CentOS上运行](http://www.10tiao.com/html/391/201709/2654069087/3.html)
	- [Tutorial: Deploy an ASP.NET Core Application on Linux with Docker](https://stormpath.com/blog/tutorial-deploy-asp-net-core-on-linux-with-docker)
	- [ASP.NET Core 网站发布到Linux服务器](http://www.cnblogs.com/keepcodingforever/p/6642183.html)
	- [ASP.NET Core 网站在Docker中运行](https://www.cnblogs.com/keepcodingforever/p/6698862.html)
	- [Quickstart: Compose and ASP.NET Core with SQL Server](https://docs.docker.com/compose/aspnet-mssql-compose/)
	- [Docker Dockerfile的使用](https://www.jianshu.com/p/93a678d1bde6)
	- [.NET 和 Docker结合使用](http://dockone.io/article/2433)
	- [将 ASP.NET 容器部署到远程 Docker 主机](https://docs.microsoft.com/zh-cn/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)
	- [Using Visual Studio Tools for Docker (Visual Studio on Windows)](https://docs.microsoft.com/en-us/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)
	- [.NET Docker Development with Visual Studio 2017](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)
	- [Build, Debug, Deploy ASP.NET Core Apps with Docker](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)
	- [Building a Microservices solution using Docker, .NET and Windows Server 2016](https://www.youtube.com/watch?v=Y2YmJTB1IKE)
1. VScode + 本地 + Docker + ASP.NET Core
1. VScode + Publish + Docker + ASP.NET Core
1. VScode + Debug + Docker + ASP.NET Core 
1. Server2016 + Docker + ASP.NET Core
1. CentOS + Docker + ASP.NET Core