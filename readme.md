## 项目介绍

1. 使用ansible管理nginx+web+mongodb+zookeeper服务的停止、更新和启动。
2. 项目的整体结构采用ansible最佳实践推荐的[组织形式](https://ansible-tran.readthedocs.io/en/latest/docs/playbooks_best_practices.html#content-organization) 。
3. staging文件配置hosts inventory，包括什么服务配置在哪台主机上，每个服务和实例的变量值。
4. ansible.cfg文件配置获取facts时的缓存，和ansible输出的格式。
5. Role check_py、env_py2、env_py3和common主要是解决环境差异问题，可以仅在机器初始化时执行一次。
6. mongodb.yml定义了mongodb服务的作业（play），使用mongodb的docker镜像。
7. zookeeper.yml定义了zookeeper服务的作业（play），使用zookeeper的docker镜像。
8. web.yml定义了web服务的作业（play），使用hello-ansible-web的docker镜像，实现参考hello-ansible-web项目。
web服务会启动3个实例，部署在不同的主机节点上，每个实例的配置通过jinja2生成，挂载到容器中。
通过zookeeper，web服务集群中有1个实例会选举成master。
9. nginx.yml定义了nginx服务的作业（play），使用nginx的docker镜像。
nginx的配置，主要是upstream服务列表的配置，通过jinja2生成，挂载到容器中。


## Ansible介绍

[Ansible介绍](docs/ansible.md)

## 问题
1. 解决python2和python3的环境差异花了我半天的时间，一直在尝试在python3的环境下使用ansible yum，解决思路不对。
2. 如果Ansible Task在执行的过程中卡主了，没有输出，不知道发生了什么事情，不清楚如何调试。
3. 不知道有没有好的方式反馈Ansible Task执行过程中的输出。
4. Ansible作为配置中心，可视化管理的能力弱，还是使用专门的配置中心比较好。

## Ansible UI

## 腾讯-蓝鲸智云

## 和Jenkins集成
```
pipeline {
    agent any
	stages {
        stage('ansible') {
            steps {
                sshagent (credentials: ['ansible-controller']) {
                    sh "ssh -v -o StrictHostKeyChecking=no root@host_ip -C \"cd ~/ansible; ansible-playbook -i staging mongodb.yml\""
                }
            }
        }
    }
}	
```