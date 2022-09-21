已停止维护
# juliet.lib android 通用框架，代号：朱丽叶
### 特色
#### 1. 基于kotlin
* 90%的代码基于kotlin
#### 2. 封装高可复用mvp模式 
* 封装了BaseActivity,BaseFragment,并增加了fragment回退栈管理，每一次返回操作，均会层层出发fragment 的onBackPressed，事件被消耗，则此次操作结束  
* 封装了BaseModel 内部包含两个内联函数，提供get/post请求，通过范性来确定返回值类型，简单易用  
* 通过范性约束model,presenter,view 三层的引用类型，并用弱应用弱化三者的强绑定，防止内存泄漏
* 封装协程控制，可通过presenter使用协程，在页面销毁时自动停止所有协程任务，避免泄漏
* 生产-消费模式管理各级页面嵌套的onResume 和 onPause 避免Fragment多层嵌套引起的方法不回调问题和事件消费模式，避免某类事件被重复处理
#### 3. 封装网络层，增加同请求缓存  
* 使用前初始化域名，application，请求公共参数等，可重复初始化
* 通过动态传递url，复用get/post请求，避免重复创建service，减少冗余代码
* 通过请求时cacheAble来控制是否启用缓存，做到单个接口单个控制，缓存会第一时间返回，之后会返回网络最新数据，并更新本地缓存
#### 4. 封装glide图片加载  
* 通过kotlin 封装glide库，进一步简化代码，增加易用性，待继续优化
#### 5. 封装常用工具
* 常用工具，包括字符串转换，表情符过滤，日志打印，软应用，弱应用权限申请等
* 新增属性动画封装，链式调用更简单
### 使用  
```
project下的gradle中添加maven库
allprojects {
    repositories {
        google()
        jcenter()
        maven { url "https://raw.githubusercontent.com/RongzhiLiu/juliet.lib/master" }
    }
}
在app的gradle中添加依赖
implementation 'com.liurongzhi:juliet:1.1.1'
```
