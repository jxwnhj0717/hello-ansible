## How Ansible Works

链接：https://www.ansible.com/overview/how-ansible-works

Ansible 是一个极其简单的 IT 自动化引擎，可自动执行云配置、配置管理、应用程序部署、服务内编排和许多其他 IT 需求。

它不使用代理，也没有额外的自定义安全基础设施，因此易于部署。 它使用yaml语言，以接近自然语言的方式描述自动化作业。

Ansible的工作原理是连接到一个节点并向它们推送称为“Ansible 模块”的小程序。 这些程序被编写为系统所需状态的资源模型。
然后 Ansible 执行这些模块（默认通过 SSH），并在完成后删除它们。

几个重要的概念：inventory、ad-hoc命令和playbook。

## 为什么使用Ansible

链接：https://www.ansible.com/resources/get-started#

### Simple

1. Human readable automation
2. No special coding skills needed
3. Tasks executed in order
4. Usable by every team
5. Get productive quickly

### Powerful

1. App deployment
2. Configuration management
3. workflow orchestration
4. Network automation
5. Orchestrate the app lifecycle

### Agentless

1. Agentless architecture
2. uses openssh & winRM
3. no agents to exploit or update
4. get started immediately
5. more efficient & more secure

## Ansible的使用场景

### 使用场景

1. [Configuration Management](https://www.ansible.com/use-cases/configuration-management)
2. [App Deployment](https://www.ansible.com/use-cases/application-deployment)
3. [Continuous Delivery](https://www.ansible.com/use-cases/continuous-delivery)
4. [Orchestration](https://www.ansible.com/use-cases/orchestration)

### 知识点

1. 【Configuration Management】Goal-oriented, not scripted. Ansible features an state-driven resource model that describes 
the desired state of computer systems and services, not the paths to get them to this state. 
2. 【Continuous Delivery】Rolling updates. Zero Downtime. 滚动更新，零停机。[参考示例](https://ansible-tran.readthedocs.io/en/latest/docs/guide_rolling_upgrade.html#lamp-rolling-upgrade) 。
3. 【Orchestration】Take this gig on the road. 一次编排，到处使用。[最佳实践-内容组织](https://ansible-tran.readthedocs.io/en/latest/docs/playbooks_best_practices.html#content-organization)
中展示了生产环境和stage环境的配置差异。
4. 【Orchestration】You've freed yourself, now go and free the others. 
通过Ansible and Ansible Tower，可以让其他人配置几个参数点击下按钮就能部署一组服务。

## Ansible的集成内容

1. Infrastructure
2. Networks
3. Containers
4. Cloud
5. DevOps Tools
6. Security

## Ansible中文文档

内容组织比较乱，但是详细介绍了Ansible的主要概念。

### 配置ssh连接

参考：https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server

参考中给出的做法并不适合自动化。

### Inventory

链接：https://ansible-tran.readthedocs.io/en/latest/docs/intro_inventory.html

定义主机，对主机分组，可以对一台或一组主机执行任务。可对主机或组定义变量。

### ad-hoc命令

链接：https://ansible-tran.readthedocs.io/en/latest/docs/intro_adhoc.html

用来执行临时命令。

### playbooks

链接：https://ansible-tran.readthedocs.io/en/latest/docs/playbooks.html

真正的Ansible脚本。最佳实践中介绍了playbooks的推荐组织形式。

### playbooks示例

链接：https://ansible-tran.readthedocs.io/en/latest/docs/guides.html

## Ansible英文文档

链接：https://docs.ansible.com/ansible_community.html

[Ansible User Guide](https://docs.ansible.com/ansible/latest/user_guide/index.html) 组织得非常好。

## 使用Ansible

实际就是了解Task的API，编写Task。

