# WHY

iPhone 5 变长了，对于手指较短的人而言，拇指很难碰到导航栏上的按钮，操作并不方便。

ShortFingerViewController 主要为 UIViewController／UITableViewController 添加 '滑动检测' 功能，让 View 能够通过向下滑动／向左滑动等动作离开 ModalView 或返回到前一个菜单，让用户不需伸长手指点击导航栏上的相应按钮。

![](https://photos-2.dropbox.com/t/0/AACCQbuQmap2_uUnu8_2UUpzi40sXYHEH-kSYkUMubyH3A/10/12114735/jpeg/1024x768/2/1350500400/0/2/Untitled.tiff/udjg1rLLGPHEcDzQp2IFWY2lDektsmVXuHtPhXsh7VU)


### [看实际效果](http://d.pr/v/7g15)

# HOW
## 开始使用 ShortFingerViewController
ShortFingerViewController 继承了 UIViewController 的全部 API。这意味着你可以不需要大面积修改您现成的代码。

1. 下载后，将 SFViewController 文件夹中的所有文件拖入您的 XCode 项目中。

2. 在需要使用 SFViewController 的 *.h 文件中使用 `#import` 导入 `SFViewController.h` 文件。如果是 UITableViewController，需要导入 `SFTableViewController.h` 文件。如：`#import "SFTableViewController.h"`

3. 将超类（Superclass）改成 SFViewController。如：`@interface MainViewController : SFViewController`

4. 通过使用 `didPanToPositionX` 或者 `didPanToPositionY` 探测用户是否进行拖动。当用户拖动界面到达一定距离时，里面的代码就会执行。示范代码如下：`- (void)didPanToPositionX{[self dismissModalViewControllerAnimated:YES];}`

只要完成以上步骤，ShortFingerViewController 就能正常运行。

## 可选项

ShortFingerViewController 自带一些可以设置的选项，其中包括

- `presentSpeed` 显示速度
- `previousViewMaskColor` 显示 ModalView 时背景 View 的背景颜色 
- `previousViewMaskAlpha` 显示 ModalView 时背景 View 的透明度
- `enableVerticalPull` 允许纵向拖动
- `enableHorizontalPull` 允许横向拖动
- `positionX` X 数值，在大于这个数值时激活 didPanToPositionX
- `positionY` Y 数值，在大于这个数值时激活 didPanToPositionY

## TableViewController

由于 TableViewController 的情况特殊，此类并没有直接继承 UITableViewController，而是继承了 SFViewController，并在此基础上添加 TableView。这样做保证了您可以为 TableView 添加背景，而不是纯黑色。

如果您需要添加背景色／背景图。您需要删除 TableView 自带的背景。代码如下 `[self.tableView setBackgroundView:[[UIView alloc]init]];`

在删除背景后，给 View 加上背景色。 如：`[self.view setBackgroundColor:[UIColor whiteColor]];`

# ME

ShortFingerViewController 是 Sean Cheng 为其项目 CloudsFM 所写的一些代码。是我第一次写 Public Code，感到非常高兴。希望您会觉得这些代码有用。遇到 BUG 请告诉我。谢谢！