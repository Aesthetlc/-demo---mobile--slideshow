# -demo---mobile--slideshow
效果案例实现移动端轮播图

### ：简单轮播图

- 需求：
  - 左划效果：图片从第n张到第n+1张
  - 右划效果：图片从第n张到第n-1张
- 左划实现：
  - 获取元素：box、ul
  - 注册事件：box注册swipeLeft 
  - 左划之后：
    - 设置全局索引，代表当前的图片的下标及显示的位置；
    - 左划，索引从当前+1，计算出ul应该出现的位移，设置给ul;
    - 同时划到最后一张时，当前下标是图片数组长度-1，再次左划，归于0；
### ：无缝轮播

- 从第6张到第1张的时候，我们想也要一个滑动过渡的效果；
- **解决：给首尾各添加一张图片；**

- 无缝原理：**
  - 当我们划到6.jpg时（实际上在HTML顺序上是倒数第二张），让用户觉得已经到最后一张了。
  - 再往左划时，会划出来1.jpg（实际上在HTML顺序上是最后一张），让用户觉得到无缝到了第一张了。
  - 这个瞬间，最后一张图片会有个过渡；
- **这个时候，我们通过一个事件（当过渡结束时），我们一瞬间把整个管理图片的父亲的位置归到1.jpg（实际上在HTML顺序上是第二张）的位置；这样就无缝完成！**
- 第一步：修改HTML结构上增加了两个子元素，css样式要改变

- 实现：
  - 获取元素：box，ul等
  - 注册事件：左右划、过渡结束
  - **划动过渡结束后：**
- 第二步：**判断当前的下标在划动过渡结束后进行判断，那么就不需要左划右划里进行判断了**；
- 第三步：默认显示HTML结构第2张，下标初始化为1；
- 第三步：**划动过渡结束后的全局的下标的值进行判断**

- 往左划时：
  - 下标为7时，显示的为HTML结构上的第8张；
  - 在过渡结束后，下标立马回到1；（下标为1，HTML显示为2）
  - 是返回去了，但是过渡效果还在；所以应该先去除过渡效果，在移动，再加上过渡效果；
