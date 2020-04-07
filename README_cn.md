
### 单机部署Docker多实例
- 容器内端口可以随机映射到主机，保证端口不冲突【可行】
- 在容器内部获取随机暴露到主机的端口【未知，TODO】
- 通过Java代码注册HTTP服务提供者到Nginx
- 设置hostname
- 在 /etc/hosts 配置hostname
- 通过Java代码注册Dubbo服务提供者到注册中心

### Ref
- https://spring.io/guides/gs/spring-boot-docker/
- https://stackoverflow.com/questions/48544373/spring-boot-get-docker-exposed-port-for-eureka-registration/53187773 【不能用】

### 操作
- cd complete/
- bash gradlew build && java -jar build/libs/gs-spring-boot-docker-0.1.0.jar 【打包、执行】
- docker build --build-arg JAR_FILE=build/libs/*.jar -t springio/gs-spring-boot-docker . 【docker打包】
- docker run -P --name gs-spring-boot-docker -t springio/gs-spring-boot-docker 【docker运行。】
```shell script
$ docker ps
CONTAINER ID        IMAGE                            COMMAND                  CREATED             STATUS              PORTS                                              NAMES
2a64817029ed        springio/gs-spring-boot-docker   "java -agentlib:jdwp…"   13 seconds ago      Up 12 seconds       0.0.0.0:32795->5005/tcp, 0.0.0.0:32794->8080/tcp   gs-spring-boot-docker
```
- docker exec -it gs-spring-boot-docker sh 【进入docker】
- docker stop gs-spring-boot-docker && docker rm gs-spring-boot-docker 【停止并删除】


