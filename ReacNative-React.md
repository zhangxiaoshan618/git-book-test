#问题
1、例子中

```
React.render();和ReactDOM.render()区别是什么？
```
```
    <script type="text/javascript" src="../build/react.js"></script>
    <script type="text/javascript" src="../build/JSXTransformer.js"></script>
    <script src="../build/react-dom.js"></script>
    <script src="../build/browser.min.js"></script>  
    
    <script type="text/javascript" src="../build/react.js"></script>
    <script type="text/javascript" src="../build/JSXTransformer.js"></script>
    
    以上两段之间有什么区别？
```

2、什么时候用“，”什么时候用“；”？

3、智能提示

4、onPress={() => this.select(1)} 和 onPress={this.select.bind(this, 1)} 的区别，箭头函数默认绑定this

5、如何继承一个组件并重写属性？

```
import {
    Image
} from 'react-native';
export default class MyImage extends Image {
	static defaultProps = {
        source: {uri: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1488780672529&di=5ddba975625d16845700ab5250d5eef8&imgtype=0&src=http%3A%2F%2Fa.hiphotos.baidu.com%2Fzhidao%2Fpic%2Fitem%2Ffaedab64034f78f087172dbc7d310a55b3191c64.jpg'},
        style: {width: 100, height: 100}
    };  // 注意这里有分号
}
```
6、RN中如何设置占位图片？

7、如果样式不符合预期，而找不到别的问题，就重新运行下即可。

8、RN中的Error对象，有错误码吗？通过什么来判断错误类型？

9、加载数据动画如何做？

10、如何隐藏tabbar?
找到RCTNavigator.m，在这个方法中

```
- (void)navigationController:(UINavigationController *)navigationController
      willShowViewController:(__unused UIViewController *)viewController
                    animated:(__unused BOOL)animated

```
最开始的地方添加如下代码：

```
RCTWrapperViewController * thisController = (RCTWrapperViewController *)viewController;
  if (navigationController.viewControllers.count > 1) {
    thisController.tabBarController.tabBar.hidden = YES;
  } else {
    thisController.tabBarController.tabBar.hidden = NO;
  }
```
11、如何获取textInput的值？

12、{...this.props}的特殊用法：

13、如何设置禁止人机交互？

14、TouchableHighlight、TouchableOpacity是否可以嵌套？
可以

15、如何下拉刷新，上拉刷新？
功能不足，需要自己封装。

16、提示界面怎么弄？

17、RN中的回调：

* block（闭包）的传递
* 点击事件的回调

18、如何获取组件的大小，和位置？

19、如何将一个组件放在另一个组件的上边？

20、如何上下联动？

21.组件的布局受到，父级，同级和子级控件的影响，封装后不一定正确使用。例如：demo中封装的搜索组件。

22、学习资料http://www.lcode.org/react-native-week-issue21/

23、block的传递的几种形式

24、如何定义一个类，如何声明属性和方法，如何重写set,get 方法，如何定义一个全局静态对象。

25、时间戳和日期相互转换；
使用Moment.js，http://momentjs.cn
时间戳转换为东八区时间：

```
let day = Moment.unix(1490172672).utc().zone(-8).format('YYYY-MM-DD HH:mm:ss');
```

官方提示这个方法已经过期了：
>
Deprecation warning: moment().zone is deprecated, use moment().utcOffset instead.

```
this.time = Moment.unix(newValue.startTime * 0.001).utcOffset(-8).format('HH:mm')
```

26、if取值

```
let obj = {'name': '123', 'age': 'man', 'book': []};
        let sex = obj.sex;
        let book;
        let dogName
        obj.book && obj.book.length > 0 && (book = obj.book[0].name);
        let  se;
        if (se = obj.sex) {
            alert('取到值了' + se);
        }else {
            alert('没取到')
        }

        if ((book = obj.book) && book.length > 0) {
            alert('取到值了' + book);
        }else {
            alert('没取到')
        }

        if (obj.dog && (dogName = obj.dog.name)) {
            alert('dogName取到值了' + dogName);
        }else {
            alert('dogName没取到值');
        }
```


27、switch() {
	case:
	break
	default:
	break
}

必须写break

28、九宫格布局：justifyContent要设置为：'flex-start'，不能设置为'space-between',否则，当只有两个子组件时布局出错。

29、如何在现有工程中加入react native?

* http://www.jianshu.com/p/85b35ca72fb2
* http://www.jianshu.com/p/3dc9d70a790f

30、对于一个半 RN 半 native 的应用（即不是通过 RN 的 navigator 跳转，而是通过原生跳转好后，再分别创建 RN 的 view），创建页面时不应该直接调用 initWithBundleURL:moduleName:initialProperties:launchOptions: 方法。因为这样每次都要创建 RCTBridge，这是一个耗时耗资源的过程。应该事先创建好 RCTBridge，在要创建页面的时候调用 initWithBridge:moduleName:initialProperties: 方法。

31、如何在Swift中导出模块和方法？

32、RN如何向原生的模块发消息？

33、如何在原生工程中加入多个RN模块？

34、在原生中加入RN，调试时报错：
Runtime is not ready for debugging.
 - Make sure Packager server is running.
- Make sure the JavaScript Debugger is running and not paused on a breakpoint or exception and try reloading again.

35、RN和原生交互的问题：

* 1、原生模块提供的方法只能是对象方法，且没有返回值；
* 2、RN提供的和原生的交互主要是指控件，即原生的View类的交互，而其他的类无法交互；
* 3、RN和原生无法相互回调执行方法。
* 4、原生到RN方向上，提供了一种用来把返回值传回给JS的回调函数（RN提供的一种固定格式的回调函数），但是还处于试验阶段，不知道会有什么问题。

36、原生到RN方向上传值(原生方法有返回值的时候如何处理？)
这种方法的问题：RN的方法全在子线程异步执行，原生数据传过来和RN原生代码不一致，需要注意线程问题。


37、RN中error处理，RN中根据哪个字段判断错误类型？

38、RN中如何处理线程问题？