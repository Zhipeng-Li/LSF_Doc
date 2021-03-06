# EGO 组件概览

可以使用 LSF 启用 EGO，以提供系统基础结构来控制和管理群集资源。

就像在一台计算机上运行的操作系统聚合并虚拟化物理资源，并将其分配给应用程序一样，EGO 可以在分布式环境中执行类似的功能。

EGO 管理逻辑和物理资源，并支持所有形式的应用程序。 EGO 管理资源的供应，使资源可供应用程序使用。

主机可以分为两类：管理节点和计算节点。 管理节点为集群提供专门服务，而计算节点运行用户作业负载。

## 管理节点

管理节点在集群内提供集群和工作负载管理服务，并且不应为用户运行工作负载。 主节点，所有候选主节点和会话管理器主机必须是管理节点。 其他管理节点，包括运行数据加载器的主机，和用于报告功能的数据清除器。所有管理节点，都在同一操作系统上运行：所有 Windows，所有 UNIX 或所有 Linux。

- ##### 主节点

  主节点是集群中安装的第一台主机。 集群的资源管理器（**vemkd**）驻留在此主机上。 主节点控制集群中其余的主机，并且是集群客户端的接口。

- ##### 候选主节点

  一次只有一台主机。 如果主节点发生故障，则另一台主机将自动接管主节点角色。 可以充当主节点的主机称为候选主节点。

- ##### 会话管理节点

  一个或多个管理节点运行会话管理器。 管理节点上每个可用插槽都有一个会话管理器。 每个应用程序有一个会话管理器。

## 计算节点

计算节点，是集群中为消费者提供计算资源的那些主机。 集群可以包含任意数量的计算节点，但必须至少具有一个计算节点。

- ##### CPU 槽位

  CPU 槽位是用于测量计算资源的单位。 一个 CPU 槽位可以在计算节点上运行一个服务实例，也可以在管理节点上运行一个会话管理器。

## 守护进程

- ##### vemkd

  在主节点上运行的 VEM 内核守护程序。 它启动其他守护程序并响应分配请求。

- ##### egosc

  v 服务控制器从 vemkd 守护程序，请求适当的资源并控制服务实例。

- ##### pem

  进程执行管理器，可用于 **vemkd** 守护程序，启动，控制和监视活动，以及收集和发送运行时资源使用情况。