# WHY Karabiner? - from a programmer's perspective Mac改键神器


**背景**：文字工作者总是会追求最大的输入效率，会对自己的键盘非常敏感。为了达到**"Type as fast as your mind"**，在硬件上必然要为自己做好全面的支持。除了换一把趁手的键盘，有时候更改键盘的键位也是十分必要的。*（回想起在win下使用ctrl lead快捷键的痛不欲生）* 这里介绍一个macOS下一个很实用的更改键位软件[Karabiner](https://www.google.com/urlsa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=2ahUKEwiltuHbnJXfAhXMabwKHWMkA9EQFjAAegQIAhAC&url=https%3A%2F%2Fpqrs.org%2Fosx%2Fkarabiner%2F&usg=AOvVaw3Q6ftWJftSWzm_7nI7FGTJ)，该项目已经在[Github](https://github.com/tekezo/Karabiner-Elements)上开源。

------

<!-- more -->

### 一. 接着说为什么要改键

其实刚才对于改键的原因说的不够清楚，在自己的习惯键位下待了很长时间后也意识不到现有键位可能会存在什么问题。我也是在长时间使用macOS标准键盘很长时间后才接触改键的，现列举标准macOS键盘键位的最大痛点（很多点也适用于Windows键盘）。

> 1. **MacBook Pro with TouchBar 无实体ESC键**

这一点在新模具的MBP推出之后在程序员圈子里就被骂的一塌糊涂，其实笔者一开始并没有觉得esc变成触控式的有什么不多，毕竟在日常情况下用esc可能也就是摸鱼看剧的时候退出全屏（逃）。直到后来接触了Vim，并尝试使用Vim作为主力编辑器，才深知实体esc的重要性。

> 1. **市面绝大多数键盘Control键位置诡异**

无法使用实体esc，其实也可以曲线救国使用 **^(control) + [ ** 来代替esc。然而市面上所有的键盘control无一例外的都会出现在左下角，这是一个很尴尬的位置，是一个违反人体工程学到极致的例子。每次敲击control都需要把小拇指曲折成一个很奇怪的形状，并且会让左手偏离主键区，极大影响输入的连贯性。对于Emacs用户，control + shift 的组合键更是家常便饭，无法想象不改键该如何流畅使用Emacs。

> 3.**几乎所有键盘delete/backspace位置都在主键区最右上角**

其实这一点并没有什么好喷的，毕竟几乎所有英语标准配列的键盘都是这个样子，但是请尝试一下在双手食指**不离开FJ两个定位键**（高效输入的重中之重）的条件下去按backspace，一般人的小指应该都没有那么长，这也直接导致我每次按backspace时都需要将自己的手腕水平顺时针旋转30度用无名指来敲击，再一次让手指离开主键区。

所以到后来我的键盘成了这样子：![karaSrc8](https://pic3.zhimg.com/80/v2-a4f3db822e497b2b2aa440136887f08c_1440w.jpg)



### 二. 大救星

键盘是个深坑，一开始大家都玩轴体，玩完轴体开始玩键帽，玩完键帽开始玩RGB，玩完RGB开始定制各种材质的外壳、定位板。然而有这么一款键盘被称作绝对的[退烧利器——HHKB](https://www.hhkeyboard.com)（并不适合大多数人）。一方面它以静电容轴独特的手感获得了众多追随者，另一方面它独特的配列和高昂的价格也让它具有了一种传奇的色彩，当然我们关注它的**[键盘配列(keyboard layout)](https://www.pfu.fujitsu.com/hhkeyboard/leaflet/images/hhkb_pro_2_keylayout.pdf):**

![karaSrc7](https://pic1.zhimg.com/80/v2-77101c224264c496a4b53d9a2cc4fb2d_1440w.jpg)

忽略掉常见60%键盘都会做的function键二层映射，hhkb削掉了方向键（我并不喜欢）。最具特色的是将control移到了capslock位置，并且下移了delete。从功能键的位置可以看出，这把键盘的确是为了一部分程序员和文字工作者打造的（为什么说是一部分，毕竟也不是所有程序员都会一直呆在editor中，也有很多人是用ide的），而且键位极度偏向于Linux和macOS环境下的开发，因此把这套配列扒下来定是极好的。

### 三. Use Karabiner

macOS下是自带修饰键工具的，只不过功能比较基础，主要是为了win键盘的适配交换一下option, command 和control： ![karaSrc2](https://pic1.zhimg.com/80/v2-2db861c330e975dd6b6410cab6ea0a69_1440w.jpg))

可以看到，系统自带的修饰键还没有办法实现我们要的所有键的替换，这个时候，Karabiner出现了。

![karaSrc1](https://picb.zhimg.com/80/v2-7e07cf091053fa9e55d7d428dad92b9d_1440w.jpg)



下载好Karabiner后launchpad会出现两个app图标，我们需要用到的是Karabiner-Element。

进入软件后在Simple Modification中就能进行简单的修改，修改的方式很简单，左栏是当前键，右栏是目标键，没有先后之分，不需要考虑object reference conflict（smirk

  ![karaSrc6](https://pic4.zhimg.com/80/v2-67d61fc737a1307031cea95cb672900c_1440w.jpg)



可以针对每一把键盘进行单独修改，也可以通过建立新的profile对不同的键盘进行分类，例如我会把手上的键盘分成mac系自带键盘的和非mac系的外接键盘：     ![karaSrc5](https://pic2.zhimg.com/80/v2-3ec0b64f2f2a6220de7b320681180b70_1440w.jpg)

当更换键盘后profile的更换也可以直接在menu bar完成：

![karaSrc3](https://pic4.zhimg.com/80/v2-7193f80c44c9749bb9c12ecc4f1223ec_1440w.jpg)

还有一个很舒服的功能，即外接键盘时可以禁用内建键盘，主要是防止把外界键盘直接放在笔记本c面上用时压到内建键盘的键（话说在ins上带有hhkb标签的多半都是这样子用的），同样的，也可以对不同的键盘进行单独设置：

![karaSrc6](https://pic1.zhimg.com/80/v2-7261880d8fd4dd545ef53f4706061cd3_1440w.jpg)

另外还有对F1-F12功能的重定义，以及超级组合键（shift按下200ms后识别成shift+control）的各种改键功能。

### 四. 文件备份

其实网络上有很多关于Karabiner的介绍文章，但是几乎没有一个文章是提到了这个内容的。首先karabiner自带的只有将当前配置文件写入系统一个备份选项，对于多文件用户十分不友好，这意味着一旦karabiner出错或用户误删导致文件丢失，需要仔重新配置一遍，非常繁琐。这里介绍一下karabiner的源文件位置：

**~/.config/karabiner/karabiner.json**

直接复制文本内容存档就好，直接建立git repo也是不错的选择。

### 五. 其他平台

For Windows: [MapKeyboard](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=2ahUKEwiPitztvpXfAhXIEbwKHRk8CdsQFjAAegQIChAB&url=https%3A%2F%2Fdownload.cnet.com%2FMapKeyboard%2F3000-2094_4-10623201.html&usg=AOvVaw29A4cvr738hfOezHx2hhVE)

For Linux: [Xmodmap](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=2ahUKEwjxjpqQv5XfAhWMerwKHZBkCiAQFjAAegQIChAB&url=https%3A%2F%2Fwiki.archlinux.org%2Findex.php%2Fxmodmap&usg=AOvVaw1E9yA0osKdy--UnNlkgiDU)



## 总结：

纯键盘输入，不用鼠标甚至减少使用trackpad来提高自己在纯文字处理中的效率，集中注意力。

通过形成自己的一套键位配置来保证双手食指始终位于FJ定位键，实现全盲打。

**MAKE THE BEST OF IT！**

