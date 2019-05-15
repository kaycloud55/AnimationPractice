### Animation类

常用函数：

* `cancel()`：取消动画

* `reset()`：将控件重置到动画开始前状态。

* `setAnimationListener(Animtion.Animationlistener listener)`：设置动画监听

  * `onAnimationEnd(Animation animation)`
  * `onAnimationRepeat(Animation animation)`
  * `onAnimationStart(Animation animation)`


#### 类型

##### Animation共有属性

所有的动画都继承自Animation类，也就是说，Animation是所有动画（scale、alpha、translate、rotate）的基类，而Animation自己是没有对应的标签的，但在它的内部仍然实现一些共有的动画属性。

* duration
* fillAfater：如果设置为true，则动画结束时，将保持动画结束时的状态。
* fillBefore：如果设置为true，则动画结束时，将还原到初始状态。默认为true。
* fillEnable：与fillBefore效果相同。
* repeatCount：取值为infinite时，表示无限循环。
* repeatMode：用于设定重复的类型，有reverse和restart两个值。其中reverse表示倒序回放，restart表示重放，并且必须与repeatCount一起使用才能看到效果。
* Interpolator：用于设置插值器。



##### Scale

* fromXScale：动画起始时，空间在X轴方向上相对自身的缩放比例，浮点值。比如，1.0代表无变化，0.5代表缩小一倍，2.0代表放大一倍。
* toXScale：类似
* fromYScale：
* toYScale
* pivotX：缩放起始点X坐标，可以是数值、百分比、百分数p三种形式，比如50、50%、50%p。如果是数值，则表示当前视图的左上角，即原点处加上50px，作为缩放起始点x轴坐标；如果是50%，则表示在当前控件左上角上加上自己宽度的50%作为缩放起始点的X轴坐标；如果是50%p，则表示在当前控件的左上角加上父控件宽度的50%作为缩放起始点X轴坐标。
* pivotY





##### Alpha

用于实现渐变透明度动画效果。

* fromAlpha：动画开始时的透明度。取值范围为0.0~1.0，0.0表示全透明，1.0表示完全不透明。
* toAlpah





##### rotate

旋转动画。

* fromDegress：动画开始旋转时的角度位置，正值代表顺时针方向的度数，负值代表逆时针方向的度数。
* toDegress
* pivotX：旋转中心的位置。
* pivotY





##### translate

位移动画。

* fromXDelta：起始点坐标。可以是数值、百分数、百分数P.
* toXDelta
* fromYDelta
* toYDelta





#### set

动画集合。

> 在set中设置repeatCount无效，必须对每个动画单独设置才有作用。





#### 插值器interpolator

动画的变化速率就是由插值器来决定的。

Interpolator只是一个接口，通过实现这个接口就可以自定义动画的速率。

常见的实现如下：

* AccelerateDecelerateIntepolator：加速减速插值器。表示在开始与结束的地方速率改变比较慢，在中间的时候加速。

* AccelerateInterpolator：加速插值器。表示在动画开始的地方速率改变比较慢，然后开始加速。

* AnticipateIntepolator：初始偏移插值器。表示在动画开始的时候向前偏移一段距离，然后应用动画。对于旋转动画而言，就是先会向反方向旋转一段距离后再应用动画。可以设置张力值tension，越大，初始的偏移量越大，而且速度越快。默认为2.

* OvershootInterpolator：结束偏移插值器。表示在动画结束时，沿动画方向继续运动一段距离后再结束动画。

* AnticipateOvershootIntepolator：开始结束偏移插值器。两者的结合。

* BounceIntepolator：弹跳插值器。模拟了控件自由落地后回调的效果。

* CycleIntepolator：循环插值器。

* DecelerateInterpolator：减速插值器。表示在动画开始的一瞬间加速到最大值，然后逐渐变慢。

* LinearInterpolator：线性插值器，也叫匀速插值器。




