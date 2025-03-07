# 定制汇聚订阅 CF-Workers-SUB

### 这个是一个通过 Cloudflare Workers 搭建，将你任意节点与多个订阅汇聚成专属于你的订阅链接

Telegram交流群：[@CMLiussss](https://t.me/CMLiussss)

## Workers 部署方法
### 1. 部署 Cloudflare Worker：

   - 在 Cloudflare Worker 控制台中创建一个新的 Worker。
   - 将 [worker.js](https://github.com/cmliu/CF-Workers-SUB/blob/main/_worker.js)  的内容粘贴到 Worker 编辑器中。


### 2. 修改 订阅入口 ：

  例如您的workers项目域名为：`sub.cmliussss.workers.dev`；
   - 通过修改 `mytoken` 赋值内容，达到修改你专属订阅的入口，避免订阅泄漏。
     ```
     let mytoken = 'auto';
     ```
     如上所示，你的订阅地址则如下：
     ```url
     https://sub.cmliussss.workers.dev/auto
     或
     https://sub.cmliussss.workers.dev/?token=auto
     ```


### 3. 添加你的节点或订阅链接：

**3.1 修改 MainData 参数示例**

 - 修改 `MainData` 参数添加你的自建节点，例如：
   
	```js
	const MainData = `
	vless://b7a392e2-4ef0-4496-90bc-1c37bb234904@cf.090227.xyz:443?encryption=none&security=tls&sni=edgetunnel-2z2.pages.dev&fp=random&type=ws&host=edgetunnel-2z2.pages.dev&path=%2F%3Fed%3D2048#%E5%8A%A0%E5%85%A5%E6%88%91%E7%9A%84%E9%A2%91%E9%81%93t.me%2FCMLiussss%E8%A7%A3%E9%94%81%E6%9B%B4%E5%A4%9A%E4%BC%98%E9%80%89%E8%8A%82%E7%82%B9
	vmess://ew0KICAidiI6ICIyIiwNCiAgInBzIjogIuWKoOWFpeaIkeeahOmikemBk3QubWUvQ01MaXVzc3Nz6Kej6ZSB5pu05aSa5LyY6YCJ6IqC54K5PuiLseWbvSDlgKvmlabph5Hono3ln44iLA0KICAiYWRkIjogImNmLjA5MDIyNy54eXoiLA0KICAicG9ydCI6ICI4NDQzIiwNCiAgImlkIjogIjAzZmNjNjE4LWI5M2QtNjc5Ni02YWVkLThhMzhjOTc1ZDU4MSIsDQogICJhaWQiOiAiMCIsDQogICJzY3kiOiAiYXV0byIsDQogICJuZXQiOiAid3MiLA0KICAidHlwZSI6ICJub25lIiwNCiAgImhvc3QiOiAicHBmdjJ0bDl2ZW9qZC1tYWlsbGF6eS5wYWdlcy5kZXYiLA0KICAicGF0aCI6ICIvamFkZXIuZnVuOjQ0My9saW5rdndzIiwNCiAgInRscyI6ICJ0bHMiLA0KICAic25pIjogInBwZnYydGw5dmVvamQtbWFpbGxhenkucGFnZXMuZGV2IiwNCiAgImFscG4iOiAiIiwNCiAgImZwIjogIiINCn0=
	`
	```
注意！`MainData`参数的特殊引号必须保留，否则代码异常。



 **3.2 修改 urls 参数示例**
 
 - 修改 `urls` 参数，在脚本中设置 `urls` 变量为 你的订阅链接 的 URL。例如：

	```js
	const urls = [
		'https://sub.xf.free.hr/auto',
 		'https://hy2sub.pages.dev',
	];
	```
注意！订阅链接内容必须为`base64`格式。

## Pages 部署方法 [视频教程](https://youtu.be/KVJgCnFp1uU)

## 变量说明
| 变量名 | 示例 | 备注 | 
|--------|---------|-----|
| LINK | vless://b7a39... vmess://ew0K... https://sub...  | 可同时放入多个节点链接与多个订阅链接, 链接之间用换行做间隔 | 
| TOKEN | auto | 快速订阅内置节点的订阅路径地址 /auto | 
| TGTOKEN | 6894123456:XXXXXXXXXX0qExVsBPUhHDAbXXXXXqWXgBA | 发送TG通知的机器人token | 
| TGID | 6946912345 | 接收TG通知的账户数字ID | 
| SUBAPI | api.v1.mk | clash、singbox等 订阅转换后端 | 
| SUBCONFIG | [https://raw.github.../ACL4SSR_Online_Full_MultiMode.ini](https://raw.githubusercontent.com/cmliu/ACL4SSR/main/Clash/config/ACL4SSR_Online_Full_MultiMode.ini) | clash、singbox等 订阅转换配置文件 | 


## 注意事项
项目中，TGTOKEN和TGID在使用时需要先到Telegram注册并获取。其中，TGTOKEN是telegram bot的凭证，TGID是用来接收通知的telegram用户或者组的id。


## Star 星星走起
[![Stargazers over time](https://starchart.cc/cmliu/CF-Workers-SUB.svg?variant=adaptive)](https://starchart.cc/cmliu/CF-Workers-SUB)


# 感谢
[mianayang](https://github.com/mianayang/myself/blob/main/cf-workers/sub/sub.js)
