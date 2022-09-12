前端项目：[ZMind思维导图](https://github.com/zyascend/ZMindMap) 的Node后端

### Features
- Koa
- Qiniu
- Mongodb
- redis
- JWT

## 下载安装使用教程
* 前置准备
	* nodejs环境
	* docker
- 安装npm依赖
```bash
npm install 
```
* 用docker简化部署所需数据库mongodb、redis的流程
* mongodb
	* 拉取镜像
		```bash
			docker pull mongo
		```
	* 启动容器（-d是后台运行 -p是端口映射 -v是加载mongodb配置文件 --name后面跟你要给该容器起的名字）
		```bash
		docker run -d -p 27017:27017 -v mongo_configdb:/data/configdb -v mongo_db:/data/db --name mongo docker.io/mongo 
	    ```
	启动后可以用datagrip等可视化数据库管理工具连接管理（mongo容器默认无密码 端口为27017）
		 mongodb://localhost:27017
		
* redis
	* 拉取镜像
		```bash
		docker pull redis
        ```
	* 启动容器
		```bash
		docker run --name redis -d -p 6379:6379 redis 
        ```
	* 测试连接(有出现127.0.0.1:6379即说明成功 可ctrl c退出)
		```bash
		redis-cli
        ```
* 运行node主程序（先cd到项目根目录）
	```bash
	npm run start
    ```
 此时终端会出现类似一下日志字样即可说明后端成功跑起来了
    ```bash
	Redis this.client: ready
	Mongodb connected!
    ```
* 之后便可以准备项目的[前端部分](https://github.com/seasnakes/ZMindMap)来连接使用后端服务
### 补充说明
* 可以用postman等工具测试API给后端发数据
* Linux服务器上可以用 sudo apt install -y docker.io 安装docker 
* config.js里放着相关图床配置，结合实际更改
* 启动docker容器前确保docker daemon已启动(就是要先点击docker图标启动app)
* ![](https://static001.geekbang.org/resource/image/c8/fe/c8116066bdbf295a7c9fc25b87755dfe.jpg?wh=1920x1048)