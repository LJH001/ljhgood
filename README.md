1、在BaseActivity中，在onCreate方法里，写方法，那么在它的子类，onCreate方法中的super.onCreate()后变开始执行父类的方法，之后才执行super.onCreate()后的方法，也就是setContentView（）；
     从以上可以看出，子类继承父类，那么回调方法一定是在父类中的某个方法中执行，例如：在父类onCreate方法里调用了抽象方法，那么子类在super.onCreate()方法里便会回调，再去执行下面的代码

2、对于报指针的问题必须要考虑到代码的执行顺序的问题，常常是异步问题，也有时是未初始化对象造成，也有时是继承父类后出现的回调方法出错，也就是可能父类写错了；

3、活用Framelayout布局，这是解决浮动控件的办法，同时在性能上来讲：FramLayout>LinearLayout>RelativeLayout

4、对于自定义标题
    a、先设置标题的布局；
    b、在activity中设置
requestWindowFeature(Window.FEATURE_CUSTOM_TITLE) ;
必须在setContentView(id)方法前；
     c、在setContentView()后加上布局
getWindow().setFeatureInt(Window.FEATURE_CUSTOM_TITLE, R.layout. title_bar);
如果要进行其它事件，可以获得组件后写
    d、设置主题（一共有两种：
                         静态设置：android:theme="@style/主题名"；
                         动态设置：
                                         setTheme(R.style.ThemeTitle );
                                          该ThemeTitle为在style中设置，也可以新建名为theme的文件，格式为Styles中的样式；
5、轮播图片在龙岗项目中dell包里

7、在TextView中使用超级连接有几种方式：
  1.TextView设置：
 autoLink：一共有几种值：web，phone, map, email, all, none.分别是url连接。电话号码提取拨号，地图地址。电子邮件，全部解释就是能支持的超级连接全部起作用，none就是默认情况，没有超链接。
android:autoLink="web" //是将文本的web网址解释成超链接
textView01.setAutoLinkMask(Linkify.ALL)； 
2.setMovementMethod，此方法在需要响应用户事件时使用，如点击一个电话号码就跳转到拨号页面。如果不执行这个方法是不会响应事件的，即便文本看着已经是下划线蓝色字了。

8、在Android中链接到另一个页面的用法 ：    

（1）、 Uri uri = Uri.parse("http://www.example.com");
 Intent intent = new Intent(Intent.ACTION_VIEW, uri);
 startActivity(intent);
（2）、
 WebView webview = new WebView(this);
webview.loadUrl(url);或者
String summary = "<html><body>You scored <b>192</b> points.</body></html>";
 webview.loadData(summary, "text/html", null);
 setContentView(webview);
(3)第7点

8、<LinearLayout>标签的android:showDividers属性

可以在LinearLayout的相应位置显示分隔线。

android:showDividers属性可以设置如下4个值：
none：不显示分隔线；
beginning：在LinearLayout的开始处显示分隔线；
end：在Linearlayout的结尾处显示分隔线；
middle：在LinearLayout中的每两个组件间显示分隔线；
9、开发遇到这样的异常问题：
(1)、android.content.res.Resources$NotFoundException:String resource ID #0x86
今天跑程序的时候，出现这样的错误：
android.content.res.Resources$NotFoundException:String resource ID #0x86

LogCat显示出错行是：
if (bet.getStatus() != null) {
            holder.statusView.setText(bet.getStatus());
}

开始的时候，死活找不出原因。
后来发现错误原因是：
           bet.getStatus()返回的是Integer类型，转成String类型，即可，如下：           
           holder.statusView.setText("" + bet.getStatus());
10、设置字体下划线
//为绑定车辆按钮设置下划线
tvHomeBind.setText(Html.fromHtml("<u>" + "去绑定" + "</u>"));
