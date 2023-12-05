# 注意事项
## 场景
验证 portal 和 work package 主从仓库的整合

## 目标
在 portal 中显示 wp 的列表或卡片，点击打开新的浏览器tab。portal和wp均有自己的路由页面。

## 工程相关
- 构建后的功能放在同级目录下（推荐）
- wp 需要根据命名空间配置 构建的path

```js
export default defineConfig({
  base: 'work-package-foo',
  // ...
})
```
跳转到 wp 的代码实现
```js
window.open(path, '_blank')
```

## nginx config
```
server {
	listen 8200;
	location / {
		root /Users/jinan/code/html/portal/dist;
		try_files $uri $uri/ /index.html;
		index index.html;
	}
	location /work-package-foo {
		alias /Users/jinan/code/html/work-package-foo/dist;
		try_files $uri $uri/ /work-package-foo/index.html;
		index  index.html index.htm;
	}
	location /work-package-bar {
		alias /Users/jinan/code/html/work-package-bar/dist;
		try_files $uri $uri/ /work-package-bar/index.html;
		index  index.html index.htm;
	}
}
```
需要注意的几个点
- 为每个wp 配置 location
- 内部路由拦截的路径与wp同名
- wp 设置alias

