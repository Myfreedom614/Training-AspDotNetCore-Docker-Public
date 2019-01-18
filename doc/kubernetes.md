## QuickStart
- [Kubernetes Basics](https://kubernetes.io/docs/tutorials/kubernetes-basics/)
- [什么是 Kubernetes？](https://www.redhat.com/zh/topics/containers/what-is-kubernetes)
- [MicroK8s Quick start](https://microk8s.io/)
	- `sudo apt update -y && sudo apt upgrade -y && sudo apt install snapd`
	- `sudo snap install microk8s --classic`

			2019-01-15T03:18:44Z INFO Waiting for restart...
			microk8s v1.13.1 from 'canonical' installed
	- `snap info microk8s`

			name:      microk8s
			summary:   Kubernetes for workstations and appliances
			publisher: Canonical✓
			contact:   https://github.com/ubuntu/microk8s
			license:   unset
			description: |
			  MicroK8s is a small, fast, secure, single node Kubernetes that installs on just about any Linux
			  box. Use it for offline development, prototyping, testing, or use it on a VM as a small, cheap,
			  reliable k8s for CI/CD. It's also a great k8s for appliances - develop your IoT apps for k8s and
			  deploy them to MicroK8s on your boxes.
			commands:
			  - microk8s.config
			  - microk8s.disable
			  - microk8s.docker
			  - microk8s.enable
			  - microk8s.inspect
			  - microk8s.istioctl
			  - microk8s.kubectl
			  - microk8s.reset
			  - microk8s.start
			  - microk8s.status
			  - microk8s.stop
			services:
			  microk8s.daemon-apiserver:          simple, enabled, active
			  microk8s.daemon-apiserver-kicker:   simple, enabled, active
			  microk8s.daemon-controller-manager: simple, enabled, active
			  microk8s.daemon-docker:             simple, enabled, active
			  microk8s.daemon-etcd:               simple, enabled, active
			  microk8s.daemon-kubelet:            simple, enabled, active
			  microk8s.daemon-proxy:              simple, enabled, active
			  microk8s.daemon-scheduler:          simple, enabled, active
			snap-id:      EaXqgt1lyCaxKaQCU349mlodBkDCXRcg
			tracking:     stable
			refresh-date: today at 03:19 UTC
			channels:                              
			  stable:         v1.13.1  (354) 229MB classic
	- `microk8s.kubectl get all`

			NAME                 TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)   AGE
			service/kubernetes   ClusterIP   10.152.183.1   <none>        443/TCP   4m32s
	- `microk8s.kubectl get no`

			NAME        STATUS   ROLES    AGE     VERSION
			testu1804   Ready    <none>   5m13s   v1.13.1
	- `microk8s.enable dns dashboard`
	- `microk8s.kubectl get all --all-namespaces`
	
			NAMESPACE   NAME                 TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)   AGE
			default     service/kubernetes   ClusterIP   10.152.183.1   <none>        443/TCP   7m34s
	- `microk8s.kubectl get all --all-namespaces`

			NAMESPACE     NAME                                                  READY   STATUS        RESTARTS   AGE
			kube-system   pod/heapster-v1.5.2-6bc7c4965d-58r8h                  0/4     Pending       0          7s
			kube-system   pod/kube-dns-6ccd496668-624g2                         0/3     Terminating   0          21s
			kube-system   pod/kube-dns-6ccd496668-fqf2w                         0/3     Pending       0          5s
			kube-system   pod/kubernetes-dashboard-654cfb4879-mlc7q             0/1     Pending       0          8s
			kube-system   pod/monitoring-influxdb-grafana-v4-6679c46745-dqq2m   0/2     Pending       0          8s
			
			NAMESPACE     NAME                           TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)             AGE
			default       service/kubernetes             ClusterIP   10.152.183.1     <none>        443/TCP             10m
			kube-system   service/heapster               ClusterIP   10.152.183.222   <none>        80/TCP              11s
			kube-system   service/kube-dns               ClusterIP   10.152.183.10    <none>        53/UDP,53/TCP       24s
			kube-system   service/kubernetes-dashboard   ClusterIP   10.152.183.75    <none>        443/TCP             11s
			kube-system   service/monitoring-grafana     ClusterIP   10.152.183.16    <none>        80/TCP              11s
			kube-system   service/monitoring-influxdb    ClusterIP   10.152.183.129   <none>        8083/TCP,8086/TCP   11s
			
			NAMESPACE     NAME                                             READY   UP-TO-DATE   AVAILABLE   AGE
			kube-system   deployment.apps/heapster-v1.5.2                  0/1     1            0           10s
			kube-system   deployment.apps/kube-dns                         0/1     1            0           23s
			kube-system   deployment.apps/kubernetes-dashboard             0/1     1            0           12s
			kube-system   deployment.apps/monitoring-influxdb-grafana-v4   0/1     1            0           11s
			
			NAMESPACE     NAME                                                        DESIRED   CURRENT   READY   AGE
			kube-system   replicaset.apps/heapster-v1.5.2-6bc7c4965d                  1         1         0       9s
			kube-system   replicaset.apps/kube-dns-6ccd496668                         1         1         0       21s
			kube-system   replicaset.apps/kubernetes-dashboard-654cfb4879             1         1         0       9s
			kube-system   replicaset.apps/monitoring-influxdb-grafana-v4-6679c46745   1         1         0       9s
	- `microk8s.kubectl run nginx --image nginx --replicas 3`
	- `microk8s.kubectl expose deployment nginx --port 80 --target-port 80 --type ClusterIP --selector=run=nginx --name nginx`
	- `wget 10.152.183.148`
	- `less index.html `
	- `microk8s.kubectl delete deployment/nginx`
	- `microk8s.kubectl get all --all-namespaces`
	- `microk8s.kubectl delete svc/nginx`
	- `curl -k https://10.152.183.75`
	- `microk8s.disable dns dashboard`
	- `microk8s.kubectl get all --all-namespaces`
	- `curl -k https://10.152.183.1`
	- `sudo snap remove microk8s`
- Docker vs K8S
	- k8s based docker engine
		- MicroK8s with Docker
	- docker-compose: 
		- 能编排多容器的APP
		- 不能实现在多个机器上进行容器的创建和管理
		- 主要是解决本地docker容器编排问题
	- docker-swarm
		- Kubernetes是一个开源的可以用来自动部署、伸缩和管理容器化应用的系统。
			- Kubernetes成组地部署和调度容器，这个组叫Pod，常见的Pod包含一个到五个容器，它们协作来提供一个 Service。
			- Kubernetes默认使用扁平的网络模式。通过让在一个相同 Pod 中的容器共享一个 IP 并使用 localhost 上的端口，允许所有的 Pod 彼此通讯。
			- Kubernetes 使用 Label 来搜索和更新多个对象，就好像对一个集合进行操作一样。
			- Kubernetes 会搭设一个 DSN 服务器来供集群监控新的服务，然后可以通过名字来访问它们。
			- Kubernetes 使用 Replication Controller 来实例化的 Pod。作为一个提升容错性的机制，这些控制器对一个服务的中运行的容器进行管理合监控。
		- Swarm: 
			- Docker的开发者现在将Docker Machine、Compose 和 Swarm 整合进了 Docker Toolbox 中。你可以对这三驾马车进行配置来让它们负责容器的配置、管理或者集群化容器。
			- Docker Swarm，是一个 Docker 的集群化工具。它通过使用一个或者多个 Docker 主机来组成一个 Swarm 集群。 Swarm 的设计是将容器打包到主机上，所以它能为更大的容器预留其他的主机资源。较之于随机地将容器调度到集群中的一个主机上，这种集群的组成方式能取得更加经济的伸缩性能。
		- 下面是 Swarm 和 Kubernetes 关键的不同点：
			- Swarm 有能将一组 Docker 引擎转变为一个虚拟的 Docker 引擎的原生能力。
			- 一个 swarm 只包含两个组件：agent 和 manager。
			- 一个集群有一个主机来运行一个 Swarm agent，另外一个主机来运行 Swarm manager。这对于运作来说是必要的，因为 manager 负责容器在主机上的编排和调度。
			- Swarm 使用一个发现机制来处理主机的发现和向集群的添加。
			- Swarm 提供了标准的 Docker API。这使得它提供了开箱即用的能力，能让所有既有的 Docker 管理工具 - 包括第三方的产品- 能自动地、透明地在多个主机上进行伸缩。
		- 细微的不同点
			- Kubernetes 和 Swarm 都能处理同一种类型的工作负载，以云原生应用的方式。
			- 一个很大的不同点是如何处理伸缩。
				- 在Kubernetes中，每一个应用层被定义成一个 Pod。一次部署或者复制控制器可以手工地或自动地处理伸缩。
				- 在Swarm中，对于单个容器的伸缩定义在 Compose 文件中。
			- 其他的不同点在于管理器系统如何处理高可用、负载均衡、应用滚动更新和回滚、日志和监控、存储、网络、服务发现以及性能合伸缩性上。

## OpenShift
- [Openshift quickstart: Django](https://github.com/sclorg/django-ex)
- [Enterprise Kubernetes for Developers](https://github.com/openshift/origin)
- [OKD](https://www.okd.io/): The Origin Community Distribution of Kubernetes that powers Red Hat OpenShift.