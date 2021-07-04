## springboot mybatis最基本注解使用

```
## src：
    ## java:
    - SpringBootApplicaiont.java
    - controller
    - service
    - repository / mapper [interface]
    - model

    ...

    ## resources:
    - application.properties / application.yaml
    - mapper [xml]
    - static
        - html
        - css
        - js
```

## controller【控制器层】

### @Controller / @RestController

- @Controller一般是**关注于返回模型和视图**
- @RestController是REST风格的Controller，一般是**关注于将JSON结果写入HTTP响应体中 / 关注于RESTful Web Service**
  - @RestController == @Controller + @ResponseBody（返回的JSON写入HTTP响应体里面）

```
@RestController
public class LoginController{
}
```

### @RequestMapping / @GetMapping / @PostMapping / @PutMapping / @DeleteMapping

对应HTTP：

- GET 【获取 》 查】
- POST 【提交 》 增】
- PUT 【放置 》 改】 
- DELETE 【删除 》 删】

### @PathVariable / @RequestParam / @RequestBody

- 路径变量【/user/12】
- 请求参数【/user?id=1&name=zhangsan】
- 请求体参数【/user】【请求数据在HTTP请求体中】

```
@RestController
public class LoginController{
	@GetMapping("user/{userId}")
	public User getUser(@PathVariable("userId") int userId){
		...
		return user;
	}
	...
}
```

## service【服务层】

### @Service

## mapper【持久层】

### @mapper

interface mapper + xml mapper

## model【模型】

lombok或者生成

## 其他

- ???
  - @Component【通用】
  - @Controller
  - @Service
  - @Repository / @Mapper
  - @Configuration
  - ...
- @Autowired【依赖注入】
