<h1>Mobile</h1>
<h3>版本1.0.4</h3>

 引用js

 方法：
 
 1. 判断是否为手机 <pre>Mobile.isMobile()</pre>

 2. 判断是否在微信 <pre>Mobile.isWeixin()</pre>

 3. 判断是否为Android系统 <pre>Mobile.isAndroid()</pre>

 4. 判断是否为Ios系统 <pre>Mobile.isIos()</pre>

 5. 判断是否为<pre>UC Mobile.isUC()</pre>   more see-> http://www.uc.cn/download/UCBrowser_User_Agent.pdf

 6. 判断是否为UC极速模式 <pre>Mobile.isUCFast()</pre>


 7. 最近浏览（已移除） 	1.0.3 移除
 <pre>Mobile.reViewCookie(name, str, count)</pre>
 记录cookie，依次存名字为name1、name2、…… 、name+count的cookie
        name:   记录的cookie名
        str:    记录的数据
        count:  最近访问允许的最大长度

    <pre>Mobile.getViewCookie(name)</pre>				返回记录多少个 name+count 的cookie

 8. 添加cookie，名、值、过期时间 1.0.3 移除
  <pre>Mobile.addCookie(name, value, expiresDays)（已移除）</pre> 


 9. 获取cookie <pre> Mobile.getCookie(name)</pre> 
 10. 删除cookie <pre> Mobile.removeCookie(name)</pre> 

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


 20. 新浪微博分享 
 	
		options.title 分享内容
		options.url String 分享链接
		options.pic String 分享图片的url
		options.ralateUid String 或 Number 相关微博Uid，如果有此项，分享内容会自动 @相关微博
		options.appkey String 或 Number 分享来源的appkey，如果有此项，会在微博正文地下，显示“来自XXX”
  		
  	Mobile.weiboShare(options)


 21. 下拉加载
    
 		Mobile.addMorePageIndex = 1;
		Mobile.addMoreComeReady = false;
	实现 单页面tab切换多个下拉加载时 需要复位以上2个属性
    
		dataJson.dataType 	json or jsonp, 缺省值为json;
		dataJson.url 		请求地址
	    dataJson.data 		请求参数
		dataJson.distance 	发起请求距离底部距离,缺省值10
		
		ele: 	显示 加载中... 的原生对象
		success: 	成功回调函数
		error: 		失败回调函数
    
	    以下参数按需设置
		    dataJson.pShow  	请求数据显示的文字,缺省值 加载中
		    dataJson.pShow2 	请求数据显示的点,缺省值 .
		    dataJson.pShowNum  	请求数据显示的点的个数,缺省值 3
		    dataJson.pNo  		请求数据的错误信息,缺省值 data.message or 暂无数据信息
		    dataJson.error  	请求失败显示,缺省值 加载失败，请刷新重试
		    dataJson.success 	请求成功显示,缺省值 已加载完
		    dataJson.message 	请求成功没数据所代表是的参数 缺省值message
    
	Mobile.addMore(dataJson, ele, success, error)
	使用示例 Mobile.addMore({
		url: 	'',
		data: 	{
			page: 	Mobile.addMorePageIndex
		}
	}, ele, fn1, fn2);

更新日志<br/>
<br/>2015-6-4
<br/>1.0.3 添加    Mobile.shuping 监测手机竖屏事件
<br/>1.0.3 添加    Mobile.getSearch(url) 
<br/>1.0.3 移除    Mobile.reViewCookie(name, str, count)、Mobile.addCookie(name, value, expiresDays)<br/>
<br/>2015-6-11
<br/>1.0.4 优化    Mobile.getSearch 参数不存在的时返回的bug
<br/>1.0.4 添加    Mobile.getData(name)

