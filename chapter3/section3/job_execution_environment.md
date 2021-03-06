# 作业运行环境

当 LSF 运行作业时，它将环境，从提交主机复制到执行主机。

执行环境包括以下信息:

- 作业所需的环境变量
- 作业开始运行的工作目录
- 其他与系统有关的环境设置，例如资源使用限制

## 共享的用户目录

为了提供透明的远程执行，LSF 命令确定用户的当前工作目录，并在远程主机上使用该目录。

## 可执行文件和 PATH 环境变量

可执行文件的搜索路径（PATH环境变量），未更改地传递到远程执行主机。

##### 注意

在混合集群中，当用户二进制目录，在不同主机类型上具有相同路径名时，LSF 效果最佳。使用相同的路径名，可使 PATH 变量在所有主机上均有效。

为了便于管理，LSF 配置文件存储在共享目录中。