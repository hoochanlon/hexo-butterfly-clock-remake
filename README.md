# hexo-butterfly-clock-remake

>  [!IMPORTANT]
> 这是基于[hexo-butterfly-clock](https://github.com/akilarlxh/hexo-butterfly-clock)、[hexo-butterfly-clock-anzhiyu](https://github.com/anzhiyu-c/hexo-butterfly-clock-anzhiyu)、
> [hexo-butterfly-clock-anzhiyu-yang](https://github.com/yjh2643408123/hexo-butterfly-clock-anzhiyu-yang) 项目修改而来的版> 本，为 hexo-theme-butterfly 添加侧边栏电子钟。原项目 `hexo-butterfly-clock-anzhiyu` 由 [anzhiyu-c](https://github.com/ anzhiyu-c) 开发，此版本在原项目基础上进行了重制。


<details>
<summary>程序逻辑与优化部分</summary>
程序逻辑：

1. 以和风天气API为执行基础。
1. 通过IP定位API拿到城市位置，通过城市位置拿到和风天气location id
1. 再通过location id获取到天气

优化部分：

* 删除了原作者无效的获取ip地址的代码
* 删除了高德地图API处理逻辑方式
* 添加了UniDreamLED.ttf字体
* 修正跨国家访问还显示中国时区时间
* 修正英文文字超出边框的问题
</details>

### 安装

【1】卸载时钟

```bash
npm uninstall hexo-butterfly-clock
npm uninstall hexo-butterfly-clock-anzhiyu 
npm uninstall hexo-butterfly-clock-anzhiyu-yang
```

【2】安装本插件：

```bash
npm install hexo-butterfly-clock-remake
```

【3】 在站点配置文件 _config.yml 或者主题配置文件 _config.butterfly.yml 中添加：

>  [!warning]
> 注：请使用自己的和风天气api host和key，本api host、key仅做功能演示。 和风天气开发者注册：
> * https://dev.qweather.com/docs/api/console/


```yml
# electric_clock
# see https://anzhiy.cn/posts/fc18.html
electric_clock:
  enable: true # 开关
  priority: 5 #过滤器优先权
  enable_page: all # 应用页面
  exclude:
       # - /posts/
       # - /about/
  layout: # 挂载容器类型
    type: class
    name: sticky_layout
    index: 0
  loading: https://cdn.cbd.int/hexo-butterfly-clock-anzhiyu/lib/loading.gif #加载动画自定义
  clock_css: https://cdn.cbd.int/hexo-butterfly-clock-remake@2.0.2/lib/clock.css
  clock_js: https://cdn.cbd.int/hexo-butterfly-clock-remake@2.0.2/lib/clock.js
  qweather_api_host: {YOUR API HOST} # 和风天气API HOST地址
  qweather_key: {YOUR KEY}  # 和风天气key
  default_city: "北京" # 默认城市，可选择你自己的城市
```


【4】 参数释义

  |参数|备选值/类型|释义|
  |:--|:--|:--|
  |priority|number|【可选】过滤器优先级，数值越小，执行越早，默认为10，选填|
  |enable|true/false|【必选】控制开关|
  |enable_page|path|【可选】填写想要应用的页面,如根目录就填'/',分类页面就填'/categories/'。若要应用于所有页面，就填`all`，默认为`all`|
  |exclude|path|【可选】填写想要屏蔽的页面，可以多个。写法见示例。原理是将屏蔽项的内容逐个放到当前路径去匹配，若当前路径包含任一屏蔽项，则不会挂载。|
  |layout.type|id/class|【可选】挂载容器类型，填写id或class，不填则默认为id|
  |layout.name|text|【必选】挂载容器名称|
  |layout.index|0和正整数|【可选】前提是layout.type为class，因为同一页面可能有多个class，此项用来确认究竟排在第几个顺位|
  |loading|URL|【可选】电子钟加载动画的图片|
  |clock_css|URL|【可选】电子钟样式CDN资源|
  |clock_js|URL|【可选】电子钟执行脚本CDN资源|
  |qweather_key|【必选】和风天气key|【必选】和风天气 key（默认使用hoochanlon）|
  |qweather_api_host|【必选】和风天气 api_host|【必选】和风天气 api_host（默认使用hoochanlon）|
  |default_city|【可选】默认城市|【可选】当默认城市为空，优先根据IP定位，填写了默认城市将优先使用默认城市的定位和天气|


### 插件重制使用到的工具

* 和风天气location id：https://github.com/qwd/LocationList/blob/master/China-City-List-latest.csv
* 免费获取IP地址API: https://github.com/ihmily/ip-info-api#address-1.3
* IP地址查询：https://tool.lu/ip
* 经纬度查询：https://jingweidu.bmcx.com
* cdn加速：
  * https://cdn.cbd.int/#/
  * https://www.jsdelivr.com/


