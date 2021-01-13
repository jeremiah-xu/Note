# Docker 容器使用
## Docker 客户端
1. docker 客户端非常简单 ,我们可以直接输入 docker 命令来查看到 Docker 客户端的所有命令选项。

```runoob@runoob:~# docker```

2. 可以通过命令 docker command --help 更深入的了解指定的 Docker 命令使用方法。

```runoob@runoob:~# docker "command" --help```

## 容器使用
1. 获取镜像
   
如果我们本地没有 ubuntu 镜像，我们可以使用 docker pull 命令来载入 ubuntu 镜像：

```$ docker pull ubuntu``` 

2. 启动容器

以下命令使用 ubuntu 镜像启动一个容器，参数为以命令行模式进入该容器：

```$ docker run -it ubuntu /bin/bash```

参数说明：

+ -i: 交互式操作。
+ -t: 终端。
+ ubuntu: ubuntu 镜像。
+ /bin/bash：放在镜像名后的是命令，这里我们希望有个交互式 Shell，因此用的是 /bin/bash。

3. 要退出终端，直接输入 exit:

```root@ed09e4490c57:/# exit```

## 查看所有的容器命令如下：

```$ docker ps -a```

## 使用 docker start 启动一个已停止的容器：

```$ docker start b750bbbcfd88``` 

## 后台运行
在大部分的场景下，我们希望 docker 的服务是在后台运行的，我们可以过 -d 指定容器的运行模式。

```$ docker run -itd --name ubuntu-test ubuntu /bin/bash```   
注：加了 -d 参数默认不会进入容器，想要进入容器需要使用指令 docker exec（下面会介绍到）

## 停止一个容器
停止容器的命令如下：    
```$ docker stop <容器 ID>```
## 停止的容器可以通过 docker restart 重启：

```$ docker restart <容器 ID>```

# 进入容器
在使用 -d 参数时，容器启动后会进入后台。此时想要进入容器，可以通过以下指令进入：

+ docker attach

+ docker exec：推荐大家使用 docker exec 命令，因为此退出容器终端，不会导致容器的停止。

attach 命令

1. 下面演示了使用 docker attach 命令。

```$ docker attach 1e560fca3906```  
注意： 如果从这个容器退出，会导致容器的停止。
exec 命令

2. 下面演示了使用 docker exec 命令。

```docker exec -it 243c32535da7 /bin/bash```    
注意： 如果从这个容器退出，容器不会停止，这就是为什么推荐大家使用 docker exec 的原因。

## 导出和导入容器
1. 导出容器

如果要导出本地某个容器，可以使用 docker export 命令。

```$ docker export 1e560fca3906 > ubuntu.tar```     
导出容器 1e560fca3906 快照到本地文件 ubuntu.tar。

2. 导入容器快照

可以使用 docker import 从容器快照文件中再导入为镜像，以下实例将快照文件 ubuntu.tar 导入到镜像 test/ubuntu:v1:

```$ cat docker/ubuntu.tar | docker import - test/ubuntu:v1```

此外，也可以通过指定 URL 或者某个目录来导入，例如：

```$ docker import http://example.com/exampleimage.tgz example/imagerepo```

## 删除容器
删除容器使用 docker rm 命令：

```$ docker rm -f 1e560fca3906```

下面的命令可以清理掉所有处于终止状态的容器。

```$ docker container prune```


# docker自动启动容器

创建容器时没有添加参数  --restart=always ，导致的后果是：当 Docker 重启时，容器未能自动启动。

Docker 命令修改

```docker container update --restart=always <容器名字>```

Docker提供了重新启动策略 来控制容器在退出时或Docker重新启动时是否自动启动。重新启动策略可确保以正确的顺序启动链接的容器。Docker建议您使用重新启动策略，并避免使用进程管理器来启动容器。

重新启动策略--live-restore与dockerd 命令的标志不同。--live-restore尽管网络和用户输入中断，但使用允许您在Docker升级期间保持容器运行。

## 使用重启策略

要为容器配置重新启动策略，请--restart在使用该docker run命令时使用该标志。--restart标志的值可以是以下任何一种：


| 旗	| 描述 |
| :-----| :----- |
| no|	不要自动重启容器。（默认）|
|on-failure	|如果容器由于错误而退出，则重新启动容器，该错误表现为非零退出代码。|
| always|	如果容器停止，请务必重启容器。如果手动停止，则仅在Docker守护程序重新启动或手动重新启动容器本身时才重新启动。（参见重启政策详情中列出的第二个项目）|
| unless-stopped|	类似于always，除了当容器停止（手动或其他方式）时，即使在Docker守护程序重新启动后也不会重新启动容器。|

### 以下示例启动Redis容器并将其配置为始终重新启动，除非明确停止或重新启动Docker。

```$ docker run -dit --restart unless-stopped redis```

### 重启政策详情

使用重启策略时请记住以下几点：

重启策略仅在容器成功启动后生效。在这种情况下，成功启动意味着容器启动至少10秒并且Docker已开始监视它。这可以防止根本不启动的容器进入重启循环。

如果手动停止容器，则会忽略其重新启动策略，直到Docker守护程序重新启动或手动重新启动容器。这是防止重启循环的另一种尝试。

重新启动策略仅适用于容器。群组服务的重新启动策略配置不同。请参阅与服务重新启动相关的 标志。

