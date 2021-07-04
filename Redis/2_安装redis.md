## 安装docker

- https://docs.docker.com/engine/install/centos/

## docker redis

```
$ docker pull redis
$ docker run --name=redis -p 6379:6379 -d redis

$ docker exec -it redis bash
>>>
	$ redis-cli
		>>>
			$ set "x" "helloworld"
			$ get "x"
```

