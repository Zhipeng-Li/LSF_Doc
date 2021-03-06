# 安全

了解 LSF 安全模型，身份验证和用户角色。

## LSF 安全模型

![LSF security modell](https://www.ibm.com/support/knowledgecenter/SSWRJV_10.1.0/lsf_foundations/authentication_authorization_lsf.jpg)

默认情况下，LSF 安全模型在内部跟踪用户帐户。 LSF 中定义的用户帐户，包括用于提供身份验证的密码和用于提供授权的已分配角色，例如管理员。

## LSF 用户角色

没有启用EGO的 LSF 支持以下用户角色：

- ##### LSF 用户

  有权将作业提交到 LSF 集群，并查看作业和群集的状态。

- ##### LSF 主要管理员

  有权执行集群范围的操作，更改配置文件，重新配置集群以及控制所有用户提交的作业。lsb.params 和lsb.hosts 等配置文件，可配置 LSF 的各个方面。

- ##### LSF 管理员

  有权执行影响其他LSF用户的操作。集群管理员可以对集群中的所有作业和队列，执行管理操作。可能没有更改 LSF 配置文件的权限。
  
  队列管理员的管理权限仅限于指定的队列。
  
  主机组的管理员管理权限仅限于指定的主机组。
  
  用户组的管理员管理权限仅限于指定的用户组。

## 启用 EGO 的 LSF 用户角色

启用 EGO 的 LSF，支持以下角色：

- ##### 集群管理员

  可以管理集群中的任何对象和工作负载。

- ##### 消费者管理员

  可以管理他们有权访问的使用者中的任何对象和工作负载。

- ##### 消费者用户

  可以在他们有权访问的使用者中运行工作负载。

用户帐户是在 EGO 中创建和管理的。 EGO 从其用户数据库授权用户。

## LSF 用户组

在可以指定 LSF 用户组的任何位置上，指定 UNIX 或 Linux 用户组，以此来直接使用任何现有的 UNIX 和 Linux 用户组。

## 外部认证

LSF 为倾向于使用外部或第三方安全机制（例如 Kerberos，LDAP 或 ActiveDirectory）的站点，提供了一个安全插件。

您可以创建自定义的 eauth 可执行文件，以提供用户，主机和守护程序的外部身份验证。 凭证是从外部安全系统传递的。还可以通过自定义的 eauth 可执行文件，来从操作系统或从诸如 Kerberos 的身份验证协议获取凭据。