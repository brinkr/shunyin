# 顺银投资前台及个人中心静态页面

## update 2017-8-16 

使用方法：

1. 起一个最简单的web服务器，如127.0.0.1:8686
2. 使用http://127.0.0.1:8686/project访问
3. 因在chrome浏览器下，file://协议不允许跨iframe访问资源
4. 在file协议下，个人中心和首页当前链接不能被标记，其他正常

添加内容：

1. ​

下载覆盖所有样式文件

2. ​

修改personal.css中`.left{display: block;}` 为`.left{display: inline-block;}`

3. ​

在header.html的`</body>`和`</html>` 之间插入：

```javascript
<script src="lib/jquery-1.12.4.min.js"></script>
	<script>
		$(document).ready(function(){
			var prop="solid 3px #c80000";
			var urlstr=window.parent.location.href;
			if(urlstr.indexOf('index')>0){
				$('.navi ul li').eq(0).css({"borderBottom":prop});
			}else if(urlstr.indexOf('capital')>0){				
				$('.navi ul li').eq(1).css({"borderBottom":prop});
			}else if(urlstr.indexOf('manager')>0){
				$('.navi ul li').eq(2).css({"borderBottom":prop});
			}else if(urlstr.indexOf('product')>0){
				$('.navi ul li').eq(3).css({"borderBottom":prop});
			}else if(urlstr.indexOf('contact')>0){
				$('.navi ul li').eq(4).css({"borderBottom":prop});
			}else if(urlstr.indexOf('login')>0){
				$('.navi ul li').eq(5).css({"borderBottom":prop});
			}
		});
	</script>
```

4. ​

注册界面我这里是正常的，可能是你哪里样式丢了，再讨论。checkbox（表单）的样式是跟随系统的，在不同浏览，不同操作系统下都会不同，大小也没法调整。如果一定要修改，我可以使用雪碧图模拟表单组件。

5. 新增页面为`phone.html` `namecheck.html` `password.html` 入口在安全中心

注册验证页面为`accheck.html`





---

* 原型要求基本完成
* 对原型进行了细微修改
* 存在部分已知的细节未完善
* 兼容全部现代浏览器，在edge浏览器下效果最佳
* 当使用chrome浏览器时，处于安全考虑，在file://协议下部分功能受限，需在http协议下访问