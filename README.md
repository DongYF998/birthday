# Birthday-Demo

#### 1. 必要配置

需要在application.yml中配置数据库,以及开源的邮件客户端

```yaml
spring:
  #数据库配置
  datasource:
    url: jdbc:mysql://111.9.131.75:23306/TEST?useUnicode=true&characterEncoding=UTF-8
    username: root
    password: Estim@b509
    driver-class-name: com.mysql.cj.jdbc.Driver
  mail:
    host: smtp.qq.com
    username: 329640258@qq.com
    password: oqrdcddibrlkbjhh
    properties:
      mail:
        smtp:
          ssl:
            enable: true
# mybatis 配置
mybatis:
  type-aliases-package: com.estim.inteligent.entity.*
  mapper-locations: classpath:mapper/*.xml
  use-generated-keys: true
  map-underscore-to-camel-case: true
  cache-enabled: false
  configuration:
    log-impl: org.apache.ibatis.logging.stdout.StdOutImpl

# 端口配置
server:
  port: 8081

```

数据库创建语句

```sql
create database TEST;
use TEST;

create table info(
	uid varchar(32) primary key,
    name varchar(32) not null,
    email varchar(32) not null,
	birthday date not null
)engine = InnoDB;
```



#### 2. 启动后上传员工生日信息txt文件

1. 文件位置 `resource `文件夹下`file.txt`.
2. 访问接口 `localhost:8081/birthday_info/upload` POST方法, 使用format-data类型传参，参数名称`file`, 类型`file`类型。

#### 3. 包结构

```java
+ com.birthday.demo
    - common : 通用类
    - controller: 控制器层
    - entity: 数据库表结构映射
    - mapper: Mapper层
    + service: 服务接口层
    	- impl: 服务实现层
    - task: 定时任务层
    - vo: ViewObject
```

