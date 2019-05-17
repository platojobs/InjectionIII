## InjectionIII
>Injection的作者John Holdsworth，1962年出生的，1984年读大学，现在56岁，大概有20多年的开发经验，2008年开始学iOS也就是46岁开始学iOS的，你还好意思以老为借口拒绝学新知识么，他的年龄和我们父辈年龄差不太多，附英文介绍及社区活跃度，太强了每天都在Coding，真心佩服这样的大佬，致敬！


>先带大家把整个`热重载过程`理一遍，首先我们修改一个文件，`Injection`工具会通过`File Watcher`监听观察文件改动，然后将改动的文件编译，打包，这时候Injection工具会给我们的App发个消息，兄弟我这边ready了，你更新下代码；我们的App收到消息后更新代码后再给`Injection`个反馈，好的大佬，代码已经更新，UI也刷新了；`Injection`收到反馈后，工具会变绿，完美的闭环式沟通。注意这里的过程，App要收消息，那么必须要有对应的代码，如何实现？App的代码如何更新？
>我们知道如果要让既有App，执行自己的代码可以通过注入动态库，静态的注入可以使用`optool`工具修改MachO的`Load Commands`然后重签，运行时可以使用`dlopen`或者`Bundle(path: "**.bundle").load()`加载，作者也正是采用这种方式，文中第一图，工具初始化，就是为了实现注入动态库。
>这里有一点需要说明一下，模拟器下iOS可加载Mac任意文件，不存在沙盒的说法，而真机设备如果加载动态库，只能加载`App.content`目录下的，换句话说，这个工具只支持模拟器，为了验证我的说法使用`lldb image list -o -f`
>查看执行这句代码后，动态库列表中多了iOSInjection，就算我们不看源码，用脚想都知道，这个库会负责和mac Injection通信




[项目开源地址](https://github.com/johnno1962/injectionforxcode)

>Injectionlll让你开发事半功倍，让你即时看到修改代码的页面效果，Injectionlll为你节省大量时间，让你开发更顺心，心情更愉悦，从而让你升职加薪、迎娶白富美、走向人生巅峰，从此告别996，双休不是梦。`Injectionlll`你值得拥有,程序员的欧莱雅！
>欣赏于React Native和Android的实时界面展示，想着iOS是否也能不需要每次Cmd+R,这不来了吗？

### 你看好了,👋👋👋👋👋👋👋👋👋👋
---
![](https://github.com/PlatoJobs/InjectionIII/blob/master/效果图.gif)

#### 1.安装InjectionIII

[InjectionIII下载](https://itunes.apple.com/cn/app/injectioniii/id1380446739?mt=12)

![图片地址](https://github.com/PlatoJobs/InjectionIII/blob/master/InjectionIII.png)

#### 2.打开Mac APP injectionIII, 点击Mac 桌面的injectionIII 图标-> Open Recent -> 选择你的项目 ，最后再选择FileWatcher（有对号即可）；

![FileWatcher](https://github.com/PlatoJobs/InjectionIII/blob/master/file_watcher.png)

#### 3.随手掏使用教程
+ 在工程里写入一下代码
```objc
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
// Override point for customization after application launch.

//根据情况做相关设置
#if DEBUG
    //    for iOS开发

    [[NSBundle bundleWithPath:@"/Applications/InjectionIII.app/Contents/Resources/iOSInjection.bundle"] load];

    //    for tvOS手表开发

    [[NSBundle bundleWithPath:@"/Applications/InjectionIII.app/Contents/Resources/tvOSInjection.bundle"] load];

    //    for masOS-Mas开发

    [[NSBundle bundleWithPath:@"/Applications/InjectionIII.app/Contents/Resources/macOSInjection.bundle"] load];

#endif

    return YES;

}
```
----
+ 又要上代码了

```objc
- (void)viewDidLoad {
[super viewDidLoad];
// Do any additional setup after loading the view, typically from a nib.

self.view.backgroundColor = [UIColor greenColor];

UIButton * redBtn = [UIButton buttonWithType:UIButtonTypeCustom];
[self.view addSubview:redBtn];
redBtn.backgroundColor =[UIColor redColor];
redBtn.frame = CGRectMake(100, 100, 100, 100);
redBtn.backgroundColor = [UIColor yellowColor];
}

//调用设置好的代码。`-(void)injected` 在这个方法里面调用
-(void)injected{
NSLog(@"I've been injected: %@", self);
NSLog(@"这里调用修改页面布局的代码，如这里调用了viewDidLoad方法");
[self viewDidLoad]; //当然也可以直接 redBtn.backgroundColor = [UIColor yellowColor];  redBtn改成全局的。
}
```
上述代码：//执行快捷键：`COMMAND + S`就可看到`[self viewDidLoad]`此方法的效果了。

#### 4. 大家有没有突然告别996. 有木有，有木有！！！ 妈妈再也不用担心我们调试UI了。
