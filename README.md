<h1>Mobile</h1>
<h3>版本1.0.6</h3>

 引用js

 方法：
 
 1. 判断是否为手机 <pre>Mobile.isMobile()</pre>

 2. 判断是否在微信 <pre>Mobile.isWeixin()</pre>

 3. 判断是否为Android系统 <pre>Mobile.isAndroid()</pre>

 4. 判断是否为Ios系统 <pre>Mobile.isIos()</pre>

 5. 判断是否为UC   1.0.6移除
 <pre>Mobile.isUC()</pre>   more see-> http://www.uc.cn/download/UCBrowser_User_Agent.pdf    

 6. 判断是否为UC极速模式   1.0.6移除
 <pre>Mobile.isUCFast()</pre>   


 7. 最近浏览（已移除） 	1.0.3 移除
 <pre>Mobile.reViewCookie(name, str, count)</pre>
 记录cookie，依次存名字为name1、name2、…… 、name+count的cookie
        name:   记录的cookie名
        str:    记录的数据
        count:  最近访问允许的最大长度

    <pre>Mobile.getViewCookie(name)</pre>				返回记录多少个 name+count 的cookie

 8. 添加cookie，名、值、过期时间 1.0.3 移除
  <pre>Mobile.addCookie(name, value, expiresDays)（已移除）</pre> 


 9. 获取cookie  1.0.6移除
 <pre> Mobile.getCookie(name)</pre>    
 10. 删除cookie  1.0.6移除 
 <pre> Mobile.removeCookie(name)</pre>  

 11. 改变地址栏参数：如果地址栏有对应参数，改变参数值并跳转，如果没有对应参数则为添加参数，自动补全?
  <pre> Mobile.changeUrl()</pre> 
 12. 获取地址栏参数,返回json格式，如果传参，则解析参数返回json格式。
  <pre> Mobile.getLocationSearch(url)</pre> 
 12.2 获取地址栏参数,返回json格式(允许同名name、无=、值为空)
  <pre> Mobile.getSearch(url)</pre> 
 示例： 
  <pre> var url = 'http://jiaju.sina.com.cn/?name="jiaju"&name&name=&name=sina&value=leju';
  Mobile.getLocationSearch(url)  ->  {"name":"jiaju","value":"leju"}
  Mobile.getSearch(url)         ->  {"name":["jiaju",undefined,"","sina"],"value":"leju"}</pre> 

 13. 获取地址栏单个参数,返回值,如没有则返回''
  <pre> Mobile.getUrlData(name)</pre> 
 13.2 获取地址栏单个参数,返回值,如没有则返回''
  <pre> Mobile.getData(name)</pre> 
  示例： 
 <pre> var url = 'http://jiaju.sina.com.cn/?name="jiaju"&name&name=&name=sina&value=leju'
  Mobile.getUrlData(name) 		-> 'jiaju'
  Mobile.getData(name) 			-> ["jiaju",undefined,"","sina"]</pre> 

 14. 获取经纬度
		opts.accuracy: 	是否高精度定位;
	    opts.timeout: 超时时间;
	    opts.maxAge: 缓存时长;
	    opts.success: 成功事件
    <pre>  Mobile.getPosition(opts)</pre> 

 15. 获取当前所在位置
	<pre>   opts.lat: 传入纬度值，如果不传，运用自身getPosition()函数获取纬度;
		opts.lng: 传入经度值  
		其他参数同 getPosition
	  Mobile.getAddress(opts)  -- 	需申请百度地图ak</pre> 
	

 16. 迷你jsonp 	回调函数参数名callback
 	<pre>opts.url 请求接口地址
 		opts.data 接口参数
 		json.time 超时时间-秒,缺省值0
 		opts.success 成功函数
 		opts.error 失败函数
 	 Mobile.jsonp(opts)</pre> 

 17. 迷你ajax
    
        opts.url 请求接口地址
 		opts.data 接口参数
 		json.type 请求格式get or post,缺省值get
		json.time 超时时间-秒,缺省值5
 		opts.success 成功函数
 		opts.error 失败函数
 	Mobile.ajax(opts)

 18. json转url并添加随机数t
  <pre>Mobile.json2url()</pre>


 19. 迫使滚动条到对应位置y ,y缺省值0,即回到顶部
    
	    options.time   回到顶部所需时间，默认 700ms
		options.type   运动方式，默认 ease-out（减速），其他ease-in（加速)、linear（匀速）
		options.y 回到距离顶部 Xpx, 默认 0;
		options.end    回调函数
	 Mobile.scrollMove(options)


更新日志<br/>
<br/>2015-6-4
<br/>1.0.3 添加    Mobile.shuping 监测手机竖屏事件
<br/>1.0.3 添加    Mobile.getSearch(url) 
<br/>1.0.3 移除    Mobile.reViewCookie(name, str, count)、Mobile.addCookie(name, value, expiresDays)<br/>
<br/>2015-6-11
<br/>1.0.4 优化    Mobile.getSearch 参数不存在的时返回的bug
<br/>1.0.4 添加    Mobile.getData(name)<br/>
<br/>2015-8-6
<br/>1.0.5 优化    Mobile.isMobile 改变判断条件替换UA判断
<br/>1.0.5 优化    Mobile.scrollMove 运动定时器改为Mobile.setTime
<br/>1.0.5 添加    Mobile.setTime(callback)
<br/>1.0.5 添加    Mobile.clearTime(id)
<br/>2016-3-16
<br/>1.0.6 移除某些不必要的东西，更加小巧精简

