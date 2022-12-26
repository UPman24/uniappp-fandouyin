# 仿抖音短视频阅读手册

### 特殊通知
- ##### 1.请用户认真阅读以下说明，千万不能混淆页面随意引入，如果你发现运行后页面样式排版错乱，大概率是引入错误喔。

- ##### 2.请App端用户将HbuilderX版本调整到3.3.9版本或3.3.9以下的版本，以规避list-cell渲染问题。

### 需求说明
在项目中内置短视频模块
### 功能说明

- #### 1.APP端
    - [x] 滑动视频播放
    - [x] 视频播放与暂停
    - [x] 滑动进度条
    - [x] 预加载视频
    - [x] 自适应视频封面
    - [x] 滑动视频小窗预览
    - [x] 无限加载视频
    - [x] 普通点赞/取消点赞
    - [x] 双击屏幕点赞
    - [x] 视频结束自动切换下一个视频
    - [x] 视频预览列表
        - [x] 请求加载视频列表
        - [x] 点击某视频播放某视频
        - [x] 视频列表内
            - [x] 滑动视频播放
            - [x] 视频播放与暂停
            - [x] 预加载视频
            - [x] 自适应视频封面
            - [x] 无限加载视频
            - [x] 普通点赞/取消点赞
            - [x] 侧滑返回
    - [x] 评论
        - [x] 评论列表
            - [x] 一级评论「含表情+GIF动图」
            - [x] 二级评论「含表情+GIF动图」
            - [x] 根据视频作者显示「作者」标志
            - [x] 展开查看回复的评论
            - [x] 根据是否是此视频作者显示二级评论「作者」标志
            - [x] 根据是否是此视频作者显示「删除」按钮
            - [x] 倒序显示评论
            - [x] 点赞/取消点赞
            - [&nbsp;&nbsp;]  评论算法
        - [x] 评论输入框
            - [x] 触摸弹起
            - [x] 点击表情展开默认emoji表情「QQ」
            - [x] 记住历史输入emoji表情「QQ」
            - [x] 上传自定义图片表情
            - [x] 点击GIF表情显示在评论框之下
            - [x] 记住历史GIF表情
            - [x] GIF表情
                - [x] 分页显示GIF表情
                - [x] 搜索GIF表情
                - [x] 点击GIF表情显示在评论框之下
                - [x] 点击搜索GIF弹起表情输入框
                - [x] 输入GIF值显示GIF表情，点击表情显示在评论框之下


- #### 2.微信小程序、H5端
    - [x] 滑动视频播放
    - [x] 视频播放与暂停
    - [x] 预加载视频
    - [x] 自适应视频封面
    - [x] 无限加载视频
    - [x] 普通点赞/取消点赞
    - [x] 双击屏幕点赞
    - [x] 视频结束自动切换下一个视频
    - [x] 视频预览列表
        - [x] 请求加载视频列表
        - [x] 点击某视频播放某视频
        - [x] 视频列表内
            - [x] 滑动视频播放
            - [x] 视频播放与暂停
            - [x] 预加载视频
            - [x] 自适应视频封面
            - [x] 无限加载视频
            - [x] 普通点赞/取消点赞
            - [x] 侧滑返回
                
### 注意说明

nvue使用详细参考官方文档[https://uniapp.dcloud.io/nvue-outline]

- #### 1.APP端

|App端|
| ------------- |
|index.nvue页面适用于：安卓、iOS|
|导入含 tabbar 页面，请在 onLoad()中修改 deleteHeigth的值。否则无法滑动|
|demo页面都为 nvue 页面，请误引入至 vue 页面中|
|App端请勾选VideoPlayer模块。否则视频无法播放|
|若出现每一个视频封面黑屏，请修改:poster="item.src+'?x-oss-process=video/snapshot,t_100,f_jpg'"为你使用的云服务视频截帧方法(默认使用阿里云)|
|导入项目运行正常，加入自己视频链接黑屏时，按照惯例请先新建项目运行到真机并在video加入你的链接，如果不正常说明你的视频链接本身存在问题或者视频格式不正确或不被支持，App端视频链接请保证在公网下运行|

`App端遇到这个有两种情况：1.没有勾选 VideoPlayer 模块。2.导入到HbuilderX的manifest.json文件有冲突。`
<img src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-bdb24c6d-8c19-4f80-8e7e-c9c9f037f131/1bbdd1d7-f65d-4584-bbc5-c810dd597e61.jpg" width="300px"/>

`解决办法如下：`
<img src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-bdb24c6d-8c19-4f80-8e7e-c9c9f037f131/8b6e3f9b-a525-4874-8973-c5560c2a4ea3.png" width="300px"/>

- #### 2.小程序/H5端

|小程序/H5端|
| ------------- |
|nvueSwiper页面适用于：手机H5、小程序|
|若出现小程序图片破裂，请修改:poster="list.src+'?x-oss-process=video/snapshot,t_100,f_jpg'"|
|小程序、H5用户请参考视频教程|

`<<测试阶段小程序用户请按照如下配置信息>>`

`1.前往小程序官网配置请求域名：https://bdb24c6d-8c19-4f80-8e7e-c9c9f037f131.bspapp.com【以免测试过程中出现测试数据无法请求的问题】`

<img src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-bdb24c6d-8c19-4f80-8e7e-c9c9f037f131/5a365dbc-a3e3-4055-8904-72ffdae5c9ff.png" width="450px"/>

`2.在开发者工具调试后，为保证性能可以启用真机预览(而非使用真机调试)，第一步配好以后才不会出现黑屏`

<img src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-bdb24c6d-8c19-4f80-8e7e-c9c9f037f131/70fa80a7-9b25-4c5e-9e0c-8e5460d9d611.png" width="450px"/>
<img src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-bdb24c6d-8c19-4f80-8e7e-c9c9f037f131/176a1173-222a-4dfb-8d4a-e6026ca607d6.png" width="450px"/>

### 插件解决问题

- ##### 解决App端视频列表上下滑动、视频自动滑动播放的难点
- ##### 解决视频播放前黑屏的问题
- ##### 解决其他短视频组件播放等待加载转圈问题。提前加载，即滑即播
- ##### 解决视频串音问题
- ##### 解决滑动问题
- ##### 优化视频播放性能
- ##### 精简进度条代码，高度自定义进度条样式

### 测试情况

- #### 安卓测试机型

|高端机型|芯片|系统|
|--------|----|----|
|华为 Mate40|麒麟9000|Android 10.0|
|红米 Note3|高通骁龙650|Android 6.0.1|
##### `说明：高端机型得益于芯片，滑动流畅，其他如上说明。低端机型由于机器太老6年前的安卓手机，滑动太快的时候会卡住，但是过一会就会好。`

- #### 苹果测试机型

|高端机型|芯片|系统|
|--------|----|----|
|iPhone12，iPad Pro2020|A14，A12Z|iOS14.5、iPadOS 14.2|
|iPhone6|A8|iOS 12.4|
##### `说明：高端机型得益于芯片，滑动流畅，其他如上说明。低端机型：6年前的苹果产品还是够挺，滑动只是略微卡顿。`

### 演示操作
- #### App端演示
<https://vkceyugu.cdn.bspapp.com/VKCEYUGU-bdb24c6d-8c19-4f80-8e7e-c9c9f037f131/451958da-e1a4-4eab-9961-f9bb58e76720.mp4>

<img src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-bdb24c6d-8c19-4f80-8e7e-c9c9f037f131/5c6c4a53-2cb2-4762-a8ca-16d25c71d1f6.png" width="200px"/>

- #### H5演示
[H5体验链接](http://shortvideo.flymusics.cn)
[浏览器限制🚫：不支持拦截视频的浏览器（如：夸克等），手机建议用QQ浏览，电脑均可]

- #### 小程序端演示
<https://vkceyugu.cdn.bspapp.com/VKCEYUGU-bdb24c6d-8c19-4f80-8e7e-c9c9f037f131/e09259f0-d68a-4c05-8a81-36f06a9154a7.mp4>

<img src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-bdb24c6d-8c19-4f80-8e7e-c9c9f037f131/d9cd8b60-17e4-4c0a-b79f-3624752f3da3.png" width="200px"/>

- #### 安卓开源体验链接
<https://vkceyugu.cdn.bspapp.com/VKCEYUGU-bdb24c6d-8c19-4f80-8e7e-c9c9f037f131/d01d4d28-aee0-4679-a20d-edba731e608b.apk>

<img src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-bdb24c6d-8c19-4f80-8e7e-c9c9f037f131/5c6c4a53-2cb2-4762-a8ca-16d25c71d1f6.png" width="200px"/>

- ##### 小世界体验链接
<https://vkceyugu.cdn.bspapp.com/VKCEYUGU-bdb24c6d-8c19-4f80-8e7e-c9c9f037f131/e2393380-93f1-4879-ba1f-1fe6d188c673.apk>

### 插件历程

- #### 至2022年12月15日，此插件已经连续更新和维护15个月。
- #### 对于如何提升播放性能，如何做到像抖音一样随滑随播，于是在github和gitee和DCloud插件市场和各个论坛，翻遍了播放插件和优化思路，很多插件发布以后都不会再进行长期维护，作者承诺此插件免费发布，并且长期维护，感谢大家对作者工作的支持。

### 视频教程
#### <https://www.bilibili.com/video/BV1gi4y12745>

### 问题反馈
- #### 最有效的方式就是加 QQ 群反馈，消息及时，解决速度快。
- #### 评论区反馈格式如下：
(如下格式才可得到有效回复)
```
使用端：App[iOS\Android]（小程序、H5）
问题描述：xxxxx
其他内容：xxxxx
```
（示例）
```
使用端：App[iOS]
问题描述：如何处理安全区高度
其他内容：【配图1】【配图2】
```

### 其他说明

- #### 代码注释已经一步一步写在代码旁边了
- #### 插件可直接粘贴复制，不影响其他功能
- #### 此插件原生实现，没有基于第三方原生插件，解决提前预播的难点，视频播放性能再次得到提升。
- #### App端插件引入了评论，这一部分仅做参考（如果需要H5、小程序请参考评论插件：https://ext.dcloud.net.cn/plugin?id=7875）
(App端引入)（uni-popup组件已经被改造了）

```javascript
<uni-popup type="bottom" ref="pinglun" @touchmove.stop.prevent="moveHandle">
    <view :style="'width: '+ windowWidth +'px; height: '+ (boxStyle.height/heightNum) +'px; background-color: #242424; border-top-left-radius: 10px; border-top-right-radius: 10px;'">
        <!-- 
         这里就是App评论组件
         -->
        <douyin-scrollview
        :Width="windowWidth"
        :Height="(boxStyle.height/1.23)"
        :deleteIOSHeight="36"
        :deleteAndroidHeight="15"
        @closeScrollview="closeScrollview"
        ></douyin-scrollview>
    </view>
</uni-popup>
```
### 付费完整仿小世界短视频版本

|模版/规格|基础版|高级版|
|--------|----|----|
|插件版|80¥(一次)|100¥(维护)|
|完整版|150¥(一次)|200¥(维护)|

[点击此处访问付费插件](https://ext.dcloud.net.cn/plugin?id=9397)

### 捐赠插件的开发

觉得不错的话快来支持一下作者吧

<img src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-bdb24c6d-8c19-4f80-8e7e-c9c9f037f131/25688f24-8b39-4128-8f62-08d75d5c9f3b.jpg" width="200px"/>

### QQ群1：953408573（此群已满）

### QQ群2：694794782





