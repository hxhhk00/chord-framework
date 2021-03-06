# 简介
  `chord-framework`开源项目由个人业余时间编写，主要对常用开源框架进行扩展，定制   
  框架的主旨是尽量简化常用开源框架的使用成本，尽量做到开箱即用   
  目前功能比较少，后续会逐渐加入模块   
  本人添加的模块是比较随机的   
  本框架类似spring-boot的结构，用户只需要引入相应的starter即可

# 功能特性
## nacos
- nacos支持按照分组和集群名进行注册服务和服务发现(测试通过，0.5.0版本发布)(已弃用，官方已经包含该功能)
- nacos配置支持对配置项添加自己的逻辑(测试通过，0.5.0版本发布)
## sentinel
- 配置信息通过nacos进行持久化
- 与nacos联动，双方均可修改配置，并进行联动
- 解决事务问题，nacos和sentinel有一方同步失败，则全部失败，不会造成数据不一致的问题
- 整合spring-cloud-gateway，sentinel关于网关的配置也同样可以和nacos联动
- 流量监控信息提供对prometheus的支持(测试通过，0.5.0版本发布)
## 分布式锁
- 支持zookeeper，redission，jedis，lettuce多种方式实现的分布式锁
- 支持独立配置，可以为分布式锁单独配置zookeeper和redis
## jwt
- 提供非常简单的方式，通过一个注解创建简单的认证服务器，资源服务器
- 验证码功能，可以独立配置redis存储验证码信息
- 支持自己扩展权限信息，比如从数据库获取
## kafka
- 提供很简单的配置，实现精确一次性语义
- 提供很简单的配置，实现kafka的事务和数据库的事务同步
- 默认使用一些比较优化的kafka参数配置
- spring-kafka没有针对micrometer的开箱即用的kafka_consumer的监控信息   
  chord将kafka_consumer从jmx中获取   
  注册为通用的micrometer，适配任何监控系统，比如prometheus
## dubbo
- dubbo的nacos注册和服务发现支持分组和集群名(测试通过，0.5.0版本发布)
- dubbo提供支持request范围的缓存(生产稳定使用，0.5.0版本发布)
## tomcat
- 可以使用tomcat启动，并且解决Resouce注解在Servlet和Filter中被识别为jndi资源的问题(生产稳定使用，0.6.0版本发布)

# 版本说明
0.4.0之前基于的第三方依赖为：</br> 
- spring-cloud-alibaba 2.1.0.RELEASE
- spring-cloud 2.0.8.RELEASE 也就是 Finchley

0.4.0之后基于的第三方依赖为：</br>
- spring-cloud-alibaba 2.2.1.RELEASE
- spring-cloud 2.2.3.RELEASE 也就是 Hoxton
    
# POM依赖
`chord-framework`提供了一个bom，使用的时候可以引用该bom，从而防止依赖上的问题
``` xml
    <dependencyManagement>

        <dependencies>

            <dependency>
                <groupId>com.chord.framework</groupId>
                <artifactId>chord-framework-dependencies</artifactId>
                <version>${chord.framework.version}</version>
                <scope>import</scope>
                <type>pom</type>
            </dependency>

        </dependencies>

    </dependencyManagement>
```

# 使用说明
详细的使用说明请看项目的wiki页面
