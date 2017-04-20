# 阿里路由 ARouter-demo 分析

阿里路由可以用于组件化开发,所以,简单的看了下代码,分析下执行过程

<ul>
<li style="display: list-item; line-height: 1.4em;"><span class="title">
<a href="#初始化" title="初始化" style="text-decoration: none; vertical-align: baseline;color: rgb(50, 105, 160);">初始化</a>
</span>
<!--span class="number">
1
</span-->
<ul>
<li style="display: list-item; line-height: 1.4em;"><span class="title">
<a href="#使用" title="使用" style="text-decoration: none; vertical-align: baseline;color: rgb(50, 105, 160);">使用</a>
</span>
<!--span class="number">
2
</span-->
</li>
<li style="display: list-item; line-height: 1.4em;"><span class="title">
<a href="#代码分析" title="代码分析" style="text-decoration: none; vertical-align: baseline;color: rgb(50, 105, 160);">代码分析</a>
</span>
<!--span class="number">
3
</span-->
<ul>
<li style="display: list-item; line-height: 1.4em;"><span class="title">
<a href="#arouter-&gt;init(application)" title="ARouter->init(Application)" style="text-decoration: none; vertical-align: baseline;color: rgb(50, 105, 160);">ARouter-&gt;init(Application)</a>
</span>
<!--span class="number">
4
</span-->
</li>
<li style="display: list-item; line-height: 1.4em;"><span class="title">
<a href="#_arouter-&gt;init(application)" title="_ARouter->init(Application)" style="text-decoration: none; vertical-align: baseline;color: rgb(50, 105, 160);">_ARouter-&gt;init(Application)</a>
</span>
<!--span class="number">
5
</span-->
</li>
<li style="display: list-item; line-height: 1.4em;"><span class="title">
<a href="#logisticscenter-&gt;init(application)" title="LogisticsCenter->init(Application)" style="text-decoration: none; vertical-align: baseline;color: rgb(50, 105, 160);">LogisticsCenter-&gt;init(Application)</a>
</span>
<!--span class="number">
6
</span-->
</li>
</ul>
</li>
</ul>
</li>
<li style="display: list-item; line-height: 1.4em;"><span class="title">
<a href="#携带参数跳转" title="携带参数跳转" style="text-decoration: none; vertical-align: baseline;color: rgb(50, 105, 160);">携带参数跳转</a>
</span>
<!--span class="number">
7
</span-->
<ul>
<li style="display: list-item; line-height: 1.4em;"><span class="title">
<a href="#使用-1" title="使用" style="text-decoration: none; vertical-align: baseline;color: rgb(50, 105, 160);">使用</a>
</span>
<!--span class="number">
8
</span-->
</li>
<li style="display: list-item; line-height: 1.4em;"><span class="title">
<a href="#代码分析-1" title="代码分析" style="text-decoration: none; vertical-align: baseline;color: rgb(50, 105, 160);">代码分析</a>
</span>
<!--span class="number">
9
</span-->
<ul>
<li style="display: list-item; line-height: 1.4em;"><span class="title">
<a href="#_arouter-&gt;build(string,string)" title="_ARouter->build(String,String)" style="text-decoration: none; vertical-align: baseline;color: rgb(50, 105, 160);">_ARouter-&gt;build(String,String)</a>
</span>
<!--span class="number">
10
</span-->
</li>
<li style="display: list-item; line-height: 1.4em;"><span class="title">
<a href="#_arouter-&gt;navigation(context,postcard,int,navigationcallback)" title="_ARouter->navigation(Context,Postcard,int,NavigationCallback)" style="text-decoration: none; vertical-align: baseline;color: rgb(50, 105, 160);">_ARouter-&gt;navigation(Context,Postcard,int,NavigationCallback)</a>
</span>
<!--span class="number">
11
</span-->
</li>
<li style="display: list-item; line-height: 1.4em;"><span class="title">
<a href="#logisticscenter-&gt;completion(postcard)" title="LogisticsCenter->completion(Postcard)" style="text-decoration: none; vertical-align: baseline;color: rgb(50, 105, 160);">LogisticsCenter-&gt;completion(Postcard)</a>
</span>
<!--span class="number">
12
</span-->
</li>
<li style="display: list-item; line-height: 1.4em;"><span class="title">
<a href="#_arouter-&gt;navigation(context,postcard,int,navigationcallback)-1" title="_ARouter->navigation(Context,Postcard,int,NavigationCallback)" style="text-decoration: none; vertical-align: baseline;color: rgb(50, 105, 160);">_ARouter-&gt;navigation(Context,Postcard,int,NavigationCallback)</a>
</span>
<!--span class="number">
13
</span-->
</li>
<li style="display: list-item; line-height: 1.4em;"><span class="title">
<a href="#interceptorserviceimpl-&gt;dointerceptions(postcard,-interceptorcallback)" title="InterceptorServiceImpl->doInterceptions(Postcard, InterceptorCallback)" style="text-decoration: none; vertical-align: baseline;color: rgb(50, 105, 160);">InterceptorServiceImpl-&gt;doInterceptions(Postcard, InterceptorCallback)</a>
</span>
<!--span class="number">
14
</span-->
</li>
<li style="display: list-item; line-height: 1.4em;"><span class="title">
<a href="#interceptorserviceimpl-&gt;_excute(int,-cancelablecountdownlatch,postcard)" title="InterceptorServiceImpl->_excute(int, CancelableCountDownLatch,Postcard)" style="text-decoration: none; vertical-align: baseline;color: rgb(50, 105, 160);">InterceptorServiceImpl-&gt;_excute(int, CancelableCountDownLatch,Postcard)</a>
</span>
<!--span class="number">
15
</span-->
</li>
<li style="display: list-item; line-height: 1.4em;"><span class="title">
<a href="#test1interceptor-&gt;process(postcard,interceptorcallback)" title="Test1Interceptor->process(Postcard,InterceptorCallback)" style="text-decoration: none; vertical-align: baseline;color: rgb(50, 105, 160);">Test1Interceptor-&gt;process(Postcard,InterceptorCallback)</a>
</span>
<!--span class="number">
16
</span-->
</li>
<li style="display: list-item; line-height: 1.4em;"><span class="title">
<a href="#_arouter-&gt;_navigation(context,postcard,int,navigationcallback)" title="_ARouter->_navigation(Context,Postcard,int,NavigationCallback)" style="text-decoration: none; vertical-align: baseline;color: rgb(50, 105, 160);">_ARouter-&gt;_navigation(Context,Postcard,int,NavigationCallback)</a>
</span>
<!--span class="number">
17
</span-->
</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>

</ul>
</li>

</ul>

## 基础功能
### 初始化
#### 使用
```
ARouter.init(getApplication());
```
#### 代码分析
跟入到```ARouter.init()```方法内
##### ARouter->init(Application)
 这个方法先根据变量判断是否需要初始化,然后做了两件事,一个是初始化log,一个是初始化```_ARouter.init(application)```

##### _ARouter->init(Application)
```
    protected static synchronized boolean init(Application application) {
        //.....
        LogisticsCenter.init(mContext, executor);
        //.....
        return true;
    }
```
这里对LogisticsCenter进行初始化

##### LogisticsCenter->init(Application)
```
     public synchronized static void init(Context context, ThreadPoolExecutor tpe) throws HandlerException {
        try {
            // These class was generate by arouter-compiler.
            List<String> classFileNames = ClassUtils.getFileNameByPackageName(mContext, ROUTE_ROOT_PAKCAGE);

            for (String className : classFileNames) {
               //根据起始字符串,判断是否需要加入到缓存中
            }

        } catch (Exception e) {

        }
    }
```
整个初始化的过程主要对logger初始化,缓存初始化


### 携带参数跳转
#### 使用
```
ARouter.getInstance().build("/test/activity2").withString("key1", "value1").navigation();
```
#### 代码分析
获取ARouter的单例,然后调用build(String path),最终会进入build(String path, String group)这个方法

##### _ARouter->build(String,String)
```
protected Postcard build(String path, String group) {//path的值为:"/test/activity2",group的值为"test";
        if (TextUtils.isEmpty(path) || TextUtils.isEmpty(group)) {
            throw new HandlerException(Consts.TAG + "Parameter is invalid!");
        } else {
        	//PathReplaceService 是用来解决运行期动态修改路由的问题;由于demo中没有它的实现类, 所以,pService==null; 最后直接返回Postcard对象
            PathReplaceService pService = ARouter.getInstance().navigation(PathReplaceService.class);
            if (null != pService) {
                path = pService.forString(path);
            }
            return new Postcard(path, group);
        }
    }


public final class Postcard extends RouteMeta {
	// Base
    private Uri uri;
    private Object tag;             // A tag prepare for some thing wrong.
    private Bundle mBundle;         // Data to transform
    private int flags = -1;         // Flags of route
    private int timeout = 300;      // Navigation timeout, TimeUnit.Second
    private IProvider provider;     // It will be set value, if this postcard was provider.
    private boolean greenChannel;
    private SerializationService serializationService;

    // Animation
    private Bundle optionsCompat;    // The transition animation of activity
    private int enterAnim;
    private int exitAnim;
}
```

Postcard 是一个包含了目标界面相关信息的类


返回Postcard后,调用了```.withString("key1", "value1")```方法,改方法用来香Postcard中的mBundle添加参数

**重点来了,调用```.navigation()```方法,会跟到_ARouter中的```.navigation()```方法**

##### _ARouter->navigation(Context,Postcard,int,NavigationCallback)
```
protected Object navigation(final Context context, final Postcard postcard, final int requestCode, final NavigationCallback callback){//参数值 context:null;requestCode:-1;callback:null;
	LogisticsCenter.completion(postcard);
}
```

然后调用```LogisticsCenter.completion(postcard);```方法

##### LogisticsCenter->completion(Postcard)
```
 public synchronized static void completion(Postcard postcard) {
        if (null == postcard) {
            throw new NoRouteFoundException(TAG + "No postcard!");
        }
		//根据"/test/activity2"为key,去map中找,看是否有对应的RouteMeta
        RouteMeta routeMeta = Warehouse.routes.get(postcard.getPath());
        if (null == routeMeta) {    // Maybe its does't exist, or didn't load.
       	    //如果,没有这个具体路径,就执行下面代码.
            //根据组名去寻找,组的文件
            Class<? extends IRouteGroup> groupMeta = Warehouse.groupsIndex.get(postcard.getGroup());  // Load route meta.
            if (null == groupMeta) {
            	//当前组名没有获取到,会抛出如下错误
                throw new NoRouteFoundException(TAG + "There is no route match the path [" + postcard.getPath() + "], in group [" + postcard.getGroup() + "]");
            } else {
                // Load route and cache it into memory, then delete from metas.
                //获取到分组文件,groupMeta对应的文件为com.alibaba.android.arouter.routes.ARouter$$Group$$test
                try {
                    //....打印log
					//获取这个文件,并实例出接口对象
                    IRouteGroup iGroupInstance = groupMeta.getConstructor().newInstance();
                    //向Warehouse.routes中加载"/test"分组下的数据
                    iGroupInstance.loadInto(Warehouse.routes);
                    //索引列表中移除当前信息,因为已经添加到内存中
                    Warehouse.groupsIndex.remove(postcard.getGroup());

                    //....打印log
                } catch (Exception e) {
                    throw new HandlerException(TAG + "Fatal exception when loading group meta. [" + e.getMessage() + "]");
                }
				//再一次调用compleyion(),此时Warehouse.routes中已经有"/test/activity2"对应界面的信息
                completion(postcard);   // Reload
            }
        } else {
        	//第二次会走到这里,并对
            postcard.setDestination(routeMeta.getDestination());
            postcard.setType(routeMeta.getType());
            postcard.setPriority(routeMeta.getPriority());
            postcard.setExtra(routeMeta.getExtra());

            Uri rawUri = postcard.getUri();
            //通过Uri方式启动,会走下面的方法
            if (null != rawUri) {   // Try to set params into bundle.
                //.....
            }
			//根据routeMeta.getType()的值,进行处理,当前例子的值为ACTIVITY
            switch (routeMeta.getType()) {//当类型为PROVIDER/FRAGMENT时,设置为绿色通道,不需要走拦截器
                case PROVIDER:
                	postcard.greenChannel();
                    break;
                case FRAGMENT:
                        postcard.greenChannel();
            }
        }
    }
```

completion 方法执行完毕,其中,主要做了两个功能:
1. 判断Warehouse.routes缓存中是否存在当前路径('/test/activity2')的信息,不存在则添加,并重新调用自身方法
2. 对Postcard的参数进行一些设置

代码返回到

##### _ARouter->navigation(Context,Postcard,int,NavigationCallback)
```
protected Object navigation(final Context context, final Postcard postcard, final int requestCode, final NavigationCallback callback){//参数值 context:null;requestCode:-1;callback:null;
        LogisticsCenter.completion(postcard);
		//....
        if (!postcard.isGreenChannel()) {//如果不是绿色通道就先执行拦截器
            interceptorService.doInterceptions(postcard, new InterceptorCallback() {
                @Override
                public void onContinue(Postcard postcard) {
                    _navigation(context, postcard, requestCode, callback);
                }

                @Override
                public void onInterrupt(Throwable exception) {
                    if (null != callback) {
                        callback.onInterrupt(postcard);
                    }
                }
            });
        } else {
            return _navigation(context, postcard, requestCode, callback);
        }
        return null;
}
```
按F5会跟入到doInterceptions()方法内,统一在这里处理拦截

##### InterceptorServiceImpl->doInterceptions(Postcard, InterceptorCallback)
```
@Override
    public void doInterceptions(final Postcard postcard, final InterceptorCallback callback) {
        if (null != Warehouse.interceptors && Warehouse.interceptors.size() > 0) {//拦截器集合不为空,并且拦截器数量大于0
			//校验
            checkInterceptorsInitStatus();

            if (!interceptorHasInit) {
                callback.onInterrupt(new HandlerException("Interceptors initialization takes too much time."));
                return;
            }

			//线程内执行
            LogisticsCenter.executor.execute(new Runnable() {
                @Override
                public void run() {
                    //线程同步辅助类,用来计次,等待
                    CancelableCountDownLatch interceptorCounter = new CancelableCountDownLatch(Warehouse.interceptors.size());
                    try {
                    	//执行具体逻辑地方,详细解析在下方
                        _excute(0, interceptorCounter, postcard);
                        //设置超时时间,并等待
                        interceptorCounter.await(postcard.getTimeout(), TimeUnit.SECONDS);
                        if (异常条件) {
                        	//....
                        } else {
                            callback.onContinue(postcard);//跳出拦截器,继续执行
                        }
                    } catch (Exception e) {
                        callback.onInterrupt(e);
                    }
                }
            });
        } else {
            callback.onContinue(postcard);//没有拦截器,直接直接执行
        }
    }
```

doInterceptions方法,主要做了三个工作
1. 校验
2. 线程内执行并等待结束
3. 线程内递归调用

继续看_excute()执行过程

##### InterceptorServiceImpl->_excute(int, CancelableCountDownLatch,Postcard)

```
	//参数:索引,辅助工具类,目标界面的Postcard
    private static void _excute(final int index, final CancelableCountDownLatch counter, final Postcard postcard) {
    	//判断缓存总拦截器数量是否大于索引数
        if (index < Warehouse.interceptors.size()) {
        	//根据索引获取拦截器
            IInterceptor iInterceptor = Warehouse.interceptors.get(index);
            //调用用户自定义拦截器内的方法,在arouter-demo中,用户自定义的拦截器是Test1Interceptor,
            iInterceptor.process(postcard, new InterceptorCallback() {
                @Override
                public void onContinue(Postcard postcard) {
                    //执行过用户自定义的拦截器后,执行这里
                    //线程同步工具计次减一
                    counter.countDown();
                    //递归调用自己,判断下一个拦截器
                    _excute(index + 1, counter, postcard);
                }

                @Override
                public void onInterrupt(Throwable exception) {
                   //被拦截之后的处理
                    postcard.setTag(null == exception ? new HandlerException("No message.") : exception.getMessage());
                    counter.cancel();
                }
            });
        }
    }
```

_excute方法就是递归自己,然后调用用户定义的拦截器,让用户去判断是否拦截,或者执行其他操作

看下Test1Interceptor中怎么处理的

##### Test1Interceptor->process(Postcard,InterceptorCallback)
```
  @Override
    public void process(final Postcard postcard, final InterceptorCallback callback) {
        if ("/test/activity4".equals(postcard.getPath())) {
        	//让用户自主选择是否拦截

            //不拦截
            //callback.onContinue(postcard);
            //拦截
            //callback.onInterrupt(null);
            //添加参数
            //postcard.withString("extra", "我是在拦截器中附加的参数");
            //callback.onContinue(postcard);
        } else {
        	//执行这里,不拦截
            callback.onContinue(postcard);
        }
    }

```


总结一下这里执行的顺序
1. 从```doInterceptions()```开始执行拦截器
	(1) 校验
    (2) 在线程池内调用```_excute()```方法
2. 执行 ```_excute()```方法
	(1) 根据索引获取拦截器
    (2) 拔处理工作交给用户自定义的拦截器
3. 执行用户自定义拦截器的```process```方法
 	(1) 用户拦截 : 执行2.(2) ```_excute()```中拦截器的回调方法```onInterrupt()```
    (2) 用户不拦截 : 执行2.(2)接下来的代码,计次减一,递归```_excute()```方法


当循环过所有拦截器以后,会调用```doInterceptions()```的回调,如果用户不打算拦截,将执行```_navigation```方法

##### _ARouter->_navigation(Context,Postcard,int,NavigationCallback)

```
private Object _navigation(final Context context, final Postcard postcard, final int requestCode, final NavigationCallback callback) {
        switch (postcard.getType()) {
            case ACTIVITY:
            	//实例化intent,添加参数,进行跳转
                break;
            case FRAGMENT:
				//实例化Fragment,并返回
        }
        return null;
    }
```

跳转完成!

## END
这套代码还是很好分析的,如果哪里写的不清楚或错误了,请联系我

* 邮件(chenxingyu1112@gmail.com)
* QQ: 1209101049


如果觉得本文对你有用,给个star呗：）<a href="https://github.com/LongMaoC/LongMaoC.github.io/blob/master/201704/arouter%E5%88%86%E6%9E%90.md">点赞</a>
