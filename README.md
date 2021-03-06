# Druid Spring Boot Starter

[![Build Status](https://img.shields.io/travis/drtrang/druid-spring-boot/master.svg?style=flat-square)](https://www.travis-ci.org/drtrang/druid-spring-boot)
[![Coverage Status](https://img.shields.io/coveralls/drtrang/druid-spring-boot/master.svg?style=flat-square)](https://coveralls.io/github/drtrang/druid-spring-boot?branch=master)
[![Maven Central](https://img.shields.io/maven-central/v/com.github.drtrang/druid-spring-boot.svg?style=flat-square)](https://maven-badges.herokuapp.com/maven-central/com.github.drtrang/druid-spring-boot)
[![GitHub Release](https://img.shields.io/github/release/drtrang/druid-spring-boot.svg?style=flat-square)](https://github.com/drtrang/druid-spring-boot/releases)
[![License](http://img.shields.io/badge/license-apache%202-blue.svg?style=flat-square)](https://github.com/drtrang/druid-spring-boot/blob/master/LICENSE)

Druid Spring Boot Starter 将帮助你在 Spring Boot 中使用 Druid。


## 依赖
```xml
<dependency>
    <groupId>com.github.drtrang</groupId>
    <artifactId>druid-spring-boot-starter</artifactId>
    <version>1.0.3</version>
</dependency>
```

## NEW !
1. 新增 ConfigFilter 的自动配置，替换 Druid 默认的 `connectionProperties` 方式
2. 完美支持多数据源 [ISSUE #2](https://github.com/drtrang/druid-spring-boot/issues/2)


## 配置
### 简单配置
在引入依赖的情况下，只需如下配置即可使用 Druid：

```yaml
spring:
  datasource:
    driver-class-name: org.h2.Driver
    url: jdbc:h2:file:./samples
    username: root
    password: 123456
```

### Druid 连接池
Druid Spring Boot Starter 会将以 `spring.datasource.druid` 为前缀的配置注入到 DruidDataSource，且 DruidDataSource 中的所有参数均可自定义。

```yaml
spring:
  datasource:
    druid:
      initial-size: 1
      min-idle: 1
      max-active: 10
      validation-query: SELECT 1
      test-while-idle: true
      test-on-borrow: false
      test-on-return: false
      pool-prepared-statements: true
      max-open-prepared-statements: 20
      use-global-data-source-stat: true
```

### Druid 高级特性
Druid Spring Boot Starter 添加了 Druid 的大部分特性，如 StatFilter、WallFilter、ConfigFilter、WebStatFilter 等，其中 StatFilter 默认打开，其它特性默认关闭，需要手动开启。

同样，每个特性的参数均可自定义，具体配置可以用 IDE 的自动提示功能或者阅读 Druid 的 [Wiki](https://github.com/alibaba/druid/wiki/%E9%A6%96%E9%A1%B5) 查看。

```yaml
spring:
  datasource:
    druid:
      slf4j:
        # 开启 Slf4jFilter
        enabled: true
      wall:
        # 开启 WallFilter
        enabled: true
        config:
          ## WallConfig 配置
          select-all-column-allow: false
      config:
        # 开启 ConfigFilter
        enabled: true
      web-stat:
        # 开启 Web 监控
        enabled: true
      aop-stat:
        # 开启 Aop 监控
        enabled: true
      stat-view-servlet:
        # 开启监控页面
        enabled: true
```

### 多数据源
1.0.2 版本新增多数据源支持，使用方式请查看 [DruidMultiDataSource.md](https://github.com/drtrang/druid-spring-boot/tree/master/docs/DruidMultiDataSource.md)。

### 配置示例
[application.yml](https://github.com/drtrang/druid-spring-boot/blob/master/druid-spring-boot-samples/src/main/resources/application.yml)


## 自动提示
Druid Spring Boot Starter 基于 `spring-boot-configuration-processor` 模块，支持 IDE 的自动提示。

自定义参数：<br>
![druid-configuration](https://user-images.githubusercontent.com/13851701/28149522-c1a3fc96-67c0-11e7-8ea7-630a8b3e5bfb.png)

参数说明：
![enabled](https://user-images.githubusercontent.com/13851701/28149525-d08955bc-67c0-11e7-916c-c8c5acd30b4a.png)

参数枚举值：
![db-type](https://user-images.githubusercontent.com/13851701/28148904-3bb9b07a-67bc-11e7-9912-c7043c2d7de7.png)


## 演示
[druid-spring-boot-samples](https://github.com/drtrang/druid-spring-boot/tree/master/druid-spring-boot-samples) 演示了 Druid Spring Boot Starter 的使用方式，可以作为参考。 


## Change Log
[Release Notes](https://github.com/drtrang/druid-spring-boot/releases)


## TODO
任何意见和建议可以提 [ISSUE](https://github.com/drtrang/druid-spring-boot/issues)，我会酌情加到 [TODO List](https://github.com/drtrang/druid-spring-boot/blob/master/TODO.md)，一般情况一周内迭代完毕。


## About Me
QQ：349096849<br>
Email：donghao.l@hotmail.com<br>
Blog：[Trang's Blog](http://blog.trang.space)
