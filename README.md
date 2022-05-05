# SpringCloud-Config

## 1. 简介
微服务需要将单体应用中的业务拆分成一个个子服务，每个服务的粒度相对较小，因此系统中会出现大量的服务。**由于每个服务都需要各自的配置信息才能运行，所以一套集中式的，动态的配置管理系统设施是必不可少的**

SpringCloud提供了==ConfigServer==来解决这个问题，为微服务架构中的微服务提供集中化的外部配置支持，配置服务器为==每个不同微服务应用==的所有环境提供了一个==中心化的外部配置==

SpringCloud Config分为==服务端==和==客户端==两部分

+ 服务端也称为分布式配置中心，是一个独立的微服务应用，用来连接配置服务器并为客户端提供获取配置信息，加密解密等访问接口

+ 客户端采用指定的配置中心来管理应用资源，以及业务相关的配置内容，在启动的时候从配置中心获取和加载配置信息来配置服务器，默认采用git来存储配置信息

SpringCloud Config的作用

+ 集中管理配置文件
+ 不同环境不同配置，动态化的配置更新，分环境部署比如dev/test/prod/beta/release
+ 运行期间动态调整配置，不再需要在每个服务部署的机器上编写配置文件，服务会向配置中心统一获取配置自己的信息
+ 当配置发生变化，服务不再需要重启即可感知到配置的变化并应用最新的配置
+ 将配置信息以REST接口的形式暴露，post和curl等访问刷新即可

## 2. 与Github整合部署
+ 在Github上新建一个Repository
+ 获取Repository的git地址：git@github.com:Huzhen757/SpringCloud-Config.git
+ 本地硬盘目录上新建git仓库并clone：`git clone git@github.com:Huzhen757/SpringCloud-Config.git`，在本地仓库中生成一个文件夹，与新建的Repository同名
+ 新建cloud-config-center3344工程，作为cloud的配置中心模块cloudConfig Center
+ POM
+ YAML
+ 主启动类
+ windows下修改host文件，增加映射：`127.0.0.1 config3344.com`(C:\Windows\System32\drivers\etc路径下的host文件)
+ 测试通过Config微服务是否可以从Github上获取配置内容
