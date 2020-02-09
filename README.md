
#前提条件

##1.(必须) 注册[Cloudflare账号](https://dash.cloudflare.com/sign-up "Cloudflare账号"), 设置 Zone ID. 记录下来,Account ID,  Zone ID,  abcd.workers.dev

abcd.workers.dev 是免费的个人二级域名

##2.(可选) 使用自己域名.在Cloudflare 后台绑定自己域名.

#步骤
## 1. 安装cloudflare的cli工具,用于管理cloudflare workers 项目代码和部署上线
npm i @cloudflare/wrangler -g
### 如果出现错误 Error: EACCES: permission denied, mkdir
npm install -g @cloudflare/wrangler --unsafe-perm=true --allow-root

##2.克隆项目
git clone https://github.com/aumb32/workers.git

## 3. 修改配置文件
cd cors/
修改 wrangler.toml

	account_id 替换为自己的
	zone_id 替换为自己的

(可选) 如果用自己的域名,假如自己域名 cors.zme.ink

	route = "" 替换为 route = "cors.zme.ink/*"
	workers_dev = true 替换为 workers_dev = false

## 4. 配置邮箱秘钥,构建,发布
wrangler config
wrangler build
wrangler publish

##5.访问地址
xxx.workers.dev，是你的子域名，xxx是你的账号
look3w.xxx.workers.dev 就是当前发布的访问链接

(可选)如果使用自定义域名，需要配置一个域名绑定CNAME：xxx.workers.dev，并开启CDN，即点亮黄云图标

##免费套餐额度

    每天 10 万个请求（UTC + 0）
    每 10 分钟 1000 个请求
    每个请求最多10ms CPU时间
    首次请求后的最低延迟






修改来源:
https://github.com/netnr/workers
