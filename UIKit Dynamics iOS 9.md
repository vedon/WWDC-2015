##UIKit Dynamics
###1）Collision Bounds

支持非矩形的碰撞,下图中表现出非矩形碰撞的效果。（不再是以前那种只能识别矩形区域的碰撞了）

![](./resource/Screen Shot 2015-06-19 at 9.08.44 AM.png)
![](./resource/Screen Shot 2015-06-19 at 9.05.35 AM.png)

###2）UIDynamicItemGroup 
![](./resource/Screen Shot 2015-06-19 at 8.47.15 AM.png)

###3）UIFieldBehavior

任何添加到设置区域的UIView 对象都会被添加上该区域所附带的动画效果。

![](./resource/Screen Shot 2015-06-19 at 8.50.25 AM.png)
![](./resource/UIFieldBehavior.gif)
###4）UIDynamicItemBehavior
DynamicItemBehivior属性：elasticity(弹性)，friction（摩擦力），density（密度），resistance（阻力），angularResistance (角度阻力)。
![](./resource/Screen Shot 2015-06-19 at 4.17.31 PM.png)
IOS 9新添加的属性：charge 和 anchored 。charge 影响你的item 在电磁场中的变现。

###5) UISnapBehavior
![](./resource/Screen Shot 2015-06-19 at 10.07.06 AM.png)


![](./resource/snap Behavior.gif)
###6) UIAttachmentBehavior
> * Distance Attachment
![](./resource/Screen Shot 2015-06-19 at 9.55.59 AM.png)
> * Limit Attachment
![](./resource/Screen Shot 2015-06-19 at 9.56.19 AM.png)
> * Fixed Attachment
![](./resource/Screen Shot 2015-06-19 at 9.56.28 AM.png)
> * Pin Attachment
![](./resource/Screen Shot 2015-06-19 at 9.57.15 AM.png)
> * Sliding Attachment
![](./resource/Screen Shot 2015-06-19 at 9.57.25 AM.png)

###7) 调试动画的新方法

![](./resource/Screen Shot 2015-06-19 at 9.21.33 AM.png)

下面展示的是动画的区域。
![](./resource/UIFieldBehavior.gif)

###8)UIVisualEffectView
可用于制作日间，夜间模式。
![](./resource/Screen Shot 2015-06-19 at 10.36.22 AM.png)

