## InjectionIII
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
[self viewDidLoad];
}
```
上述代码：//执行快捷键：`COMMAND + S`就可看到`[self viewDidLoad]`此方法的效果了。

#### 4. 大家有没有突然告别996. 有木有，有木有！！！ 妈妈再也不用担心我们调试UI了。
