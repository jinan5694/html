## 场景
验证 portal 和 work package 主从仓库整合技术方案

## 目标
在 portal 中显示 wp 的卡片列表，点击卡片新页签打开 `wp`。`portal` 和 `wp` 均有自己的路由页面，且刷新无副作用。

## 部署
`portal` 项目按常规方式部署

### 新建 `work package`
1. 根据唯一的 `work-package-name` 创建仓库
2. 配置仓库的`base`公共基础路径
3. 跟 `portal` 部署在相同目录下
4. 在 `nginx` 中为 `work package` 添加新的配置并 `reload`


```js
export default defineConfig({
  base: '/work-package-foo/',
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


