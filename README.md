
最近开始玩GitHub欢迎Starts, Forks, Follow

[![GitHub stars](https://img.shields.io/github/stars/cesarferreira/dryrun.svg?style=social&label=Star)](https://github.com/CPUdream/dryrun)

[![GitHub forks](https://img.shields.io/github/forks/cesarferreira/dryrun.svg?style=social&label=Fork)](https://github.com/cesarferreira/dryrun/fork) [![GitHub followers](https://img.shields.io/github/followers/cesarferreira.svg?style=social&label=Follow)](https://github.com/cesarferreira/dryrun)
## Android编程规范
### 入门
本规范参考了大量前人的成果.但又不局限于此。本规范没有完全按照Java推荐的命名规则而来，而是结合了自身的实际和许多.NET规范中很多优秀的经验而制定。

### 2.3定义和约定

1. Pascal标记法
第1个字符大写，其后每个单词的第1个字母大写
2. camel标记法
第1个字符小写，其后每个单词的第1个字母大写

首先,命名总的原则是名称应该说明“什么”而不是“如何”, 从命名中可以直观看懂其定义和用途（否则必须增加注释说明）；命名要足够长以同其它变量相分别,简要描述其意义,但要足够短以避免太长；类，方法，变量不得用大小写来区分各种实体（eclipse中，在同一目录下，默认排斥以大小写来区分的类名、包名）以下是几个方面的命名规范。

### 文件命名
c 类
类的名字必须由大写字母开头而单词中的其他字母均为小写；如果类名称由多个单词组成，则每个单词的首字母均应为大写(UpperCamelCase) 对于继承于Android组件的类命名必须以Android组件结尾。例子：SignInActivity、 SignInFragment、ImageUploaderService、ChangePasswordDialog. 不可以写成: SignInAct、 SignInFrag.
#### 资源文件
资源文件名必须由小写字母和下划线组成（lowercase_underscore）

| Asset Type   | Prefix            |		Example               |
|--------------| ------------------|-----------------------------|
| Action bar   | `ab_`             | `ab_stacked.9.png`          |
| Button       | `btn_`	            | `btn_send_pressed.9.png`    |
| Dialog       | `dialog_`         | `dialog_top.9.png`          |
| Divider      | `divider_`        | `divider_horizontal.9.png`  |
| Icon         | `ic_`	            | `ic_star.png`               |
| Menu         | `menu_	`           | `menu_submenu_bg.9.png`     |
| Notification | `notification_`	| `notification_bg.9.png`     |
| Tabs         | `tab_`            | `tab_pressed.9.png`         |

icons的命名规范(出自Android iconography guidelines)


| Asset Type                      | Prefix             | Example                      |
| --------------------------------| ----------------   | ---------------------------- |
| Icons                           | `ic_`              | `ic_star.png`                |
| Launcher icons                  | `ic_launcher`      | `ic_launcher_calendar.png`   |
| Menu icons and Action Bar icons | `ic_menu`          | `ic_menu_archive.png`        |
| Status bar icons                | `ic_stat_notify`   | `ic_stat_notify_msg.png`     |
| Tab icons                       | `ic_tab`           | `ic_tab_recent.png`          |
| Dialog icons                    | `ic_dialog`        | `ic_dialog_info.png`         |

选择器的命名规范

| State	       | Suffix          | Example                     |
|--------------|-----------------|-----------------------------|
| Normal       | `_normal`       | `btn_order_normal.9.png`    |
| Pressed      | `_pressed`      | `btn_order_pressed.9.png`   |
| Focused      | `_focused`      | `btn_order_focused.9.png`   |
| Disabled     | `_disabled`     | `btn_order_disabled.9.png`  |
| Selected     | `_selected`     | `btn_order_selected.9.png`  |

### Layout文件
Layout文件一般与我们的Activity等类对应举个例子：SignInActivity.java, 写成布局文件为activity_sign_in.xml

| Component        | Class Name             | Layout Name                   |
| ---------------- | ---------------------- | ----------------------------- |
| Activity         | `UserProfileActivity`  | `activity_user_profile.xml`   |
| Fragment         | `SignUpFragment`       | `fragment_sign_up.xml`        |
| Dialog           | `ChangePasswordDialog` | `dialog_change_password.xml`  |
| AdapterView item | ---                    | `item_person.xml`             |
| Partial layout   | ---                    | `partial_stats_bar.xml`       |
说明：AdapterView必须以item_开头， 当我们创建的布局是其他布局的一部分那么这个Layout必须命名为partial_

### Menu文件
和Layout文件相似，Menu文件应该是匹配和你的组件。如果我们写了一个menu文件被用在UserActivity, 这个Menu命名为activity_user.xml(不能是menu_user, 因为Android的Menu文件已经放在Menu文件夹下).

### Values 文件

资源文件必须是复数(plural). 例如：strings.xml, styles.xml, colors.xml, dimens.xml, attrs.xml

### 代码规范
#### Java代码规范
如果按照下面格式书写代码可以形成Javadoc。javadoc是Sun公司提供的一个技术，它从程序源代码中抽取类、方法、成员等注释形成一个和源代码配套的API帮助文档。所以必须遵守。
##### 版权申明
每个文件顶部应该有一个版权申明，下面是package 和 import声明它们三个代码块之间用空行格开(blank line), 最后才是class 或者 interface 申明

### Import顺序
Import导包AndroidStudio已经设置好了，但是这里要强调一下自己手动导包事项
+ 关于Android系统相关的包必须在早上面
+ 接下来是Java相关的包
+ 最后才是第三方的jar包
+ 以上三个之间必须有一个空行分开，并且按照字母顺序
//此处举例子

### 字段定义命名
字段应该被定义在文件的顶部，遵守驼峰命名法他们还必须遵守下面的命名规范
Private , non-static字段必须以m开头
Private, static字段必须以s开头
其它类型字段开始以小写字母开头不能加m, s  //有待修改
Static final字段必须是大写加下划线(ALL_CAPS_WITH_UNDERSCORES)
```java
public class MyClass {
    public static final int SOME_CONSTANT = 42;
    public int publicField;
    private static MyClass sSingleton;
    int mPackagePrivate;
    private int mPrivate;
    protected int mProtected;
}
```
有时我们用缩略词作为字段名更已读但必须遵守一下规则

| Good           | Bad            |
| -------------- | -------------- |
| `XmlHttpRequest` | `XMLHTTPRequest` |
| `getCustomerId`  | `getCustomerID`  |
| `String url`     | `String URL`     |
| `long id`        | `long ID`        |

### 标准大括号
这个主要是针对于学过C语言的国内用户，由于大学课程大部分用的谭浩强的C程序设计，代码风格写的一塌糊涂，我只想说真正的C语言发明者写的这本书 《C程序设计语言》被评为编程必看书籍。大学教育渣！！！！
正确写法如下：
```java
class MyClass {
    int func() {
        if (something) {
            // ...
        } else if (somethingElse) {
            // ...
        } 
    }
}
```
if语句必须写成下面的
if (condition) {
    body();
}
不能写成下面的形式
```java
if (condition) body();
```
更不能写成下面的形式
```java
if (condition)
    body();  // bad!
```
### 限制行长度
Google官方规定一行不能超过100个字符,AndroidStudio不要担心这个事了，AndroidStudio中大家肯定会看到一条细细的限制线。但是下面两种情况必须是例外：
+ 如果注释中包括一个URL,这个URL长度大于100也不可以分割成两行，为了方便复制、黏贴
+ Import lines can go over the limit because humans rarely see them (this also simplifies tool writing).

### 缩进问题
缩进不以TAB为标准，一般4 space，例如：
```java
if (x == 1) {
    x++;
}
```
但是下面这种情况必须是8个空格
Instrument i =
        someLongExpression(that, wouldNotFit, on, one, line);
### 异常处理

### XML代码规范
#### 标签自我关闭
当一个XML元素没有任何内容时，必须自己关闭标签
正确写法如下：
```xml
<TextView
    android:id="@+id/text_view_profile"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" />
```
错误写法如下：
```xml
<TextView
    android:id="@+id/text_view_profile"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" >
</TextView>
```
### 资源命名
资源ids和名字必须命名为小写字母和下划线
### ID naming

| Element            | Prefix            |
| -----------------  | ----------------- |
| `TextView`           | `text_`             |
| `ImageView`          | `image_`            |
| `Button`             | `button_`           |
| `Menu`               | `menu_`             |
举两个例子：
```xml
<ImageView
    android:id="@+id/image_profile"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" />
```
```xml
<menu>
    <item
        android:id="@+id/menu_done"
        android:title="Done" />
</menu>
```

### Strings
字符串的命名必须是有
| Prefix             | Description                           |
| -----------------  | --------------------------------------|
| `error_`             | An error message                      |
| `msg_`               | A regular information message         |
| `title_`             | A title, i.e. a dialog title          |
| `action_`            | An action such as "Save" or "Create"  |

### Styles and Themes
好像和类的命名一样，后续更新

### 属性顺序
1.View id
2.Style
3.Layout width and layout height
4.其他布局属性，按字母排序
5.其他属性，按字母排序

### 建议
以下内容为建议，由于个人习惯我希望在项目完结时可以在项目之下建立一个doc文件夹把项目需求文件放进去。当然在该文件夹下能用Markdown写一个说明文档最好，文档名字都想好了叫ReadMe.md。该文档包括项目中使用到的最厉害技术、最好的效果也就是GIF图片，还包括项目存在的不足待改进的地方。

### 参考文献
[Android开源编程规范]https://source.android.com/source/code-style.html
[Java编程规范说明]
