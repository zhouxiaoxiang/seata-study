# seata-study

  主要目的是展示seata在平台微服务代码中的使用。
  
## 技术栈

  使用了以下技术

- Druid
- shardingsphere
- mybatis
- seata

## 注意事项

  seata与shardingsphere结合使用时，与seata单独使用时的内部原理区别很大。

  注意不要使用shardingsphere事务注解的方式，会导致seata无效（可以去看sharding-transaction-base-seata-at的代码）。

## 数据库

- 创建 seata0、seata1
- 运行 seata.sql

## seata服务器

1. 下载[seata-server](https://github.com/seata/seata/releases)
2. 启动seata-server: ./bin/seata-server.sh -p 8091

## 微服务测试(使用任意的HTTP测试工具)

1. 启动服务: service1、service2

2. 正常测试: 
   POST http://localhost:6000
   money=10 
   userId=1

3. 异常测试: 
   POST http://localhost:6000
   money=10
   userId=11

## 微服务关系

微服务 service1 调用 service2，构成分布式事务。
测试数据库采用分库分表，简单起见，分成了2库4表。
