Language: [English](README-EN.md) | 中文简体

## Fitness（个人项目，暂未开源）
Flutter开发的微博客户端，同时支持Android和iOS。与官方微博x9.99%相似度体验，离线模式，多语言支持，主题随心换，超乎想象的流畅度，各种惊喜的细节等待你一一发现。

### 支持功能：
查看微博动态、正文、评论  
查看热门话题、微博、热搜  
支持话题、@、表情、全文  
离线模式  
国际化  
主题色


### 项目动态
应用于2020.05.06提交至微博开发平台，目前还在审核中，暂无法申请微博授权!  
ps：作者也不清楚是否能通过审核，何时通过审核，但大家还是可以本地体验相关功能。  
目前运动和消息板块未开发，运动板块暂时放的实时疫情，消息板块展示九宫格示例。

### 分享内容

##### 1、九宫格图片控件（源码整理中，稍等···）
类似微博动态，微信朋友圈，微信群组，钉钉群组，支持单张大图预览。

#### 2、拖拽九宫格图片控件（源码整理中，稍等···）
类似微博/微信发布动态九宫格，支持按压放大效果，拖拽排序，拖拽到指定位置删除。

#### 3、获取图片尺寸 [ImageUtil](https://github.com/Sky24n/flustars)
大图功能必备工具。
```yaml
Image image = new Image(image: new CachedNetworkImageProvider("Url"));
Image imageAsset = new Image.asset("");
Image imageFile = new Image.file(File("path"));
Image imageNetwork = new Image.network("url");
Image imageMemory = new Image.memory(null);

ImageUtil imageUtil = ImageUtil();
Rect rect = await imageUtil.getImageSize(image: image);  
ImageUtil().getImageSize(image: image).then((Rect rect) {
  print("rect: " + rect.toString();
});

```

#### 4、简单加解密 [EncryptUtil](https://github.com/Sky24n/common_utils)
异或对称加解密 + Base64加解密
```yaml
const String key = '11, 22, 33, 44, 55, 66';
String value = 'Sky24n';
String encode = EncryptUtil.xorBase64Encode(value, key); // WH1YHgMs
String decode = EncryptUtil.xorBase64Decode(encode, key); // Sky24n
```
#### 5、[JsonUtil](https://github.com/Sky24n/common_utils)
简单封装json字符串转对象。
```yaml
String objStr = "{\"name\":\"成都市\"}";
City hisCity = JsonUtil.getObj(objStr, (v) => City.fromJson(v));

String listStr = "[{\"name\":\"成都市\"}, {\"name\":\"北京市\"}]";
List<City> cityList = JsonUtil.getObjList(listStr, (v) => City.fromJson(v));
```

#### 6、时间格式化 [DateUtil](https://github.com/Sky24n/common_utils)
格式化时间戳。
```yaml
/// year -> yyyy/yy   month -> MM/M    day -> dd/d
/// hour -> HH/H      minute -> mm/m   second -> ss/s

DateUtil.formatDateMs(DateTime.now().millisecondsSinceEpoch, format: DataFormats.full); // 2019-07-09 16:51:14
DateUtil.formatDateStr("2019-07-09 16:51:14", format: "yyyy/M/d HH:mm:ss"); // 2019/7/9 16:51:14
DateUtil.formatDate(DateTime.now(), format: "yyyy/MM/dd HH:mm:ss");  // 2019/07/09 16:51:14
DateUtil.formatDateMs(ms, format: "yyyy年MM月dd日 HH时mm分ss秒");  // 2019年07月09日 16时51分14秒
```
#### 7、时间轴 [TimelineUtil](https://github.com/Sky24n/common_utils)
类似微信朋友圈，微博动态时间线。
```yaml
enum DayFormat {
  ///(less than 10s->just now)、x minutes、x hours、(Yesterday)、x days.
  ///(小于10s->刚刚)、x分钟、x小时、(昨天)、x天.
  Simple,

  ///(less than 10s->just now)、x minutes、x hours、[This year:(Yesterday/a day ago)、(two days age)、MM-dd ]、[past years: yyyy-MM-dd]
  ///(小于10s->刚刚)、x分钟、x小时、[今年: (昨天/1天前)、(2天前)、MM-dd],[往年: yyyy-MM-dd].
  Common,

  ///日期 + HH:mm
  ///(less than 10s->just now)、x minutes、x hours、[This year:(Yesterday HH:mm/a day ago)、(two days age)、MM-dd HH:mm]、[past years: yyyy-MM-dd HH:mm]
  ///小于10s->刚刚)、x分钟、x小时、[今年: (昨天 HH:mm/1天前)、(2天前)、MM-dd HH:mm],[往年: yyyy-MM-dd HH:mm].
  Full,fitness_rec_list.json
}

TimelineUtil.format(timeMillis, locale: Localizations.localeOf(context).languageCode, dayFormat: DayFormat.Common);
```

#### 8、版本升级功能（仅供参考） [VersionUtil](https://github.com/Sky24n/FlutterRepos)
[dio](https://pub.flutter-io.cn/packages/dio) + [install_apk_plugin](https://pub.flutter-io.cn/packages/install_apk_plugin)    
[VersionUtil](base_library/lib/src/util/version_util.dart) + [UpgradeDialog](base_library/lib/src/ui/dialog/upgrade_dialog.dart)

### Screenshots

截图无法查看？  
掘金地址：[Flutter 仿微博客户端](https://juejin.im/post/5ebd74b5f265da7bbd2f9aa6)  
简书地址：[Flutter 仿微博客户端](https://www.jianshu.com/p/0f761fe6ad66)

|首页|探索|我的|
|:---:|:---:|:---:|
|<img src="screenshots/home.png" width="220" height="465"/>|<img src="screenshots/discover.png" width="220" height="465"/>|<img src="screenshots/me.png" width="220" height="465"/>|
|微博发布|微博正文|个人页面|
|<img src="screenshots/wb_publish.gif" width="220" height="391"/>|<img src="screenshots/wb_content.gif" width="220" height="391"/>|<img src="screenshots/wb_user.gif" width="220" height="391"/>|
|授权|设置|图片|
|<img src="screenshots/wb_auth.png" width="220" height="465"/>|<img src="screenshots/setting.png" width="220" height="465"/>|<img src="screenshots/wb_photo.png" width="220" height="465"/>|

### 关于App
GitHub &nbsp;&nbsp;： [Fitness](https://github.com/Sky24n/Fitness)  
Apk &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;：[v0.0.1](https://github.com/Sky24n/Doc/blob/master/apks/fitness.apk) (arm64-v8a)  
百度云盘：[提取码 ttbn](https://pan.baidu.com/s/1HgBaR68oJYe7nnOTJlSg0Q)  
其他方式：[v0.0.1](https://github.com/Sky24n/Doc) 

### 关于作者
GitHub : [Sky24n](https://github.com/Sky24n)  
简书 &nbsp;&nbsp;&nbsp;&nbsp;: [Sky24n](https://www.jianshu.com/u/cbf2ad25d33a)  
掘金 &nbsp;&nbsp;&nbsp;&nbsp;: [Sky24n](https://juejin.im/user/5b9e8a92e51d453df0440422)

### 意见与反馈
大家在使用中有任何问题，bug或者有需要改进但地方，可以提交[issues](https://github.com/Sky24n/Fitness/issues)反馈。  
当然也可以通过微博[私信](https://weibo.com/u/3743796227)反馈。

### 常见问题
1.微博授权过程中可能发生闪退！  
&nbsp;&nbsp;&nbsp;已知问题！重新点授权即可。（设备：乐视1s）  
2.如何退出微博登录？  
&nbsp;&nbsp;&nbsp;长按帐号栏，点击确定即可，同时微博授权会被回收。  
3.部分页面没有返回键，如何返回上一个页面？  
&nbsp;&nbsp;&nbsp;可以使用侧滑（右滑）返回，也可以使用手机Back键返回。  
4.探索页面没有回退按钮，如何返回上一个页面？  
&nbsp;&nbsp;&nbsp;双击探索Tab即可。

