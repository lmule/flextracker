## 安装
```
$ npm i
$ npm run build
```

## 使用

``` html
<script>
  window.flexTracker = {
    token: 'testtoken-123-456-789'
  }
</script>
<script  src="./tracker.js"></script>
<script>
  window.flexTracker.userdata('name', 'liuzhen')
</script>
```

token是必须的，这也是服务端区分不同用户的凭据

默认的配置如下：

``` js
var defaults = {
  enabled: true,      // 是否可用，关闭以后不再捕获和发送错误信息
  action: true,       // 是否监控并发送用户操作信息
  net: true,          // 是否hook ajax请求
  dependence: true,   // 是否发送页面上的依赖库信息，默认会有几个内置流行库的检测，剩余的通过遍历window对象获取
  compress: true,     // 是否压缩提交的数据，使用https://github.com/pieroxy/lz-string 整体性价比兼容性都比较靠谱
  autoStart: true,    // 自动开始，不想自动开始的话就设置成false，然后手动start
  report: {
    delay: 5000       // 报告发送的延迟时间(单位ms)，如果一个时间段内有很多报告产生，那么就放到一起发送
  },
  ignoreErrors: [],   // 可忽略的错误
  ignoreUrls:[],      // 可忽略的url，那些产生错误的url
}
```
## Q&A

不想自动开始监控？先设置autoStart为false

``` js
window.flexTracker = {
  token: 'testtoken-123-456-789',
  autoStart: false
}
```

然后，手动开启`window.flexTracker.start()`
