## 一、导入mysql + mybatis启动依赖

```
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.16</version>
</dependency>
<dependency>
    <groupId>org.mybatis.spring.boot</groupId>
    <artifactId>mybatis-spring-boot-starter</artifactId>
    <version>2.1.4</version>
</dependency>
```



## 二、配置数据源 + mybatis

```
# spring
server.port=10000

# datasource
spring.datasource.url=jdbc:mysql://localhost:3306/springboot_mybatis_reactjs
spring.datasource.username=root
spring.datasource.password=root
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

#mybatis
mybatis.type-aliases-package=com.example.springbootmybatisreactjs.model
mybatis.mapper-locations=classpath:mapper/*.xml # 指定mybatis mapper的位置
```

## 三、使用

> TIPS: IDEA中下载个插件：[free mybatis plugin](https://plugins.jetbrains.com/plugin/index?xmlId=cn.wuzhizhan.plugin.mybatis)

1. mapper/xxxMapper.java 【springboot mapper / **interface mapper**】
2. mapper/xxxMapper.xml 【mybatis mapper / **xml mapper**】【[mybatis xml格式](https://mybatis.org/mybatis-3/getting-started.html)】【TIPS：IDEA中可以添加mybatis xml模板，下次直接新建】

> TIPS：在xml mapper中namespace对应mapper接口 / id对应接口里面的方法【这样就接口mapper和xml mapper就连通起来了】

.java【然后直接在**interface mapper**中通过插件生成 ===>>> **xml mapper**：】

```
@Mapper
public interface UserMapper {

    User getUser(int userId);

    boolean postUser(User user);

    boolean putUser(User user);

    boolean deleteUser(User user);

}
```

.xml【然后写sql语句就完事了】

```
    <insert id="postUser"></insert>
    <update id="putUser"></update>
    <delete id="deleteUser"></delete>
    <select id="getUser" resultType="com.example.springbootmybatisreactjs.model.User"></select>
```

## TODO

### 生成 / 返回自增ID

```
interface:
int postUser(User user);

xml:
<insert id="postUser" parameterType="com.example.springbootmybatisreactjs.model.User" 
            useGeneratedKeys="true"
            keyProperty="id">
        insert into user(username, password, email, sex, age, status)
        values (#{username},
                #{password},
                #{email},
                #{sex},
                #{age},
                #{status})
</insert>
    
》》》mapper接口返回之后【自增ID会被注入到参数的user的id属性里面，也就是keyProperty设置的】

int effectRowNum = userMapper.postUser(user);
int returnId = user.getId();

return new HashMap<String, Integer>() {{
    put("effectRowNum", effectRowNum);
    put("returnId", returnId);
}};
```

- useGeneratedKeys="true"

- keyProperty的值表示的是将获取到的自增主键值(xml) => 赋给JavaBean中的某个字段(interface)【mybatis想要获取返回主键，需要一个JavaBean接受返回值】

### 驼峰式表示法



### 接口向xml中传递值

```
int postUser(User user);

》》》直接注入属性值就行了
》》》返回的ID会通过接口中参数传递回去（自动赋值）

<insert id="postUser"
            parameterType="com.example.springbootmybatisreactjs.model.User"
            useGeneratedKeys="true"
            keyProperty="id">
        insert into user(username, password, email, sex, age, status)
        values (#{username},
                #{password},
                #{email},
                #{sex},
                #{age},
                #{status})
    </insert>
```

### mysql重置自增ID和索引

清空table数据：`truncate table_name`【注意：delete不会删除索引和自增ID】

### mybatis数据注入#/$的区别

```
比如：truncate的时候，#注入就没用
```

