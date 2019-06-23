> CSS3 中使用 transform 可以对元素进行变换。其中包含：位移、旋转、偏移、缩放。 transform 可以使用 translate/rotate/skew/scale 的方式来控制元素变换，也可以使用 matrix 的方式来控制元素变换。

> 比如index中的box1和box2。

> Matrix 的中文是矩阵，是一个数学术语，在计算机科学中，会用矩阵来对象量进行变换，在 CSS3 的 transform 属性中，可以使用矩阵对图像进行变换。


##### 矩阵长什么样子
> 矩阵就是一些列的数字按照矩形排列。在数学中，矩阵用方括号包裹起来。

##### CSS3 里的 matrix 如何和矩阵对应呢
> 为什么要用矩阵来表示转换呢？因为在计算机科学中，矩阵可以对向量进行转换。矩阵中的每一个数字，对向量的转换都会产生影响。
CSS3 里面可以用矩阵表示 2D 和 3D 转换，这里只讲 2D。

```css
selector {
    transform: matrix(a, b, c, d, e, f);
}
/* 
     a  c  e

     b  d  f

     0  0  1       
 */


 /* 
 2D 的转换是由一个 3*3 的矩阵表示的，前两行代表转换的值，分别是 a b c d e f，要注意是竖着排的，第一行代表 x 轴发生的变化，第二行代表 y 轴发生的变化，第三行代表 z 轴发生的变化，因为这里是 2D 不涉及 z 轴，所以这里是 0 0 1。
 
 */
```

> （一）缩放 scale(x, y)：缩放对应的是矩阵中的 a 和 d，x 轴的缩放比例对应 a，y 轴的缩放比例对应 d。

```css
    transform: scale(x,y);

    /* a=x d=y */
    /* 所以 scale(1.5, 2) 对应的矩阵是： */
    /* 
        1.5  0   e
 
        0    2   0 

        0    0   1
    
    */
    transform: matrix(1.5, 0, 0, 2, 0, 0);
    /* 如果一个没有元素没有被缩放，默认a=1 d=1。 */
```

> （二）平移 translate(10, 20)：平移对应的是矩阵中的 e 和 f，平移的 x 和 y 分别对应 e 和 f。平移只会影响 e 和 f 值。

> （三） 旋转 rotate(θdeg)：旋转影响的是a/b/c/d四个值，分别是
transform: rotate(θdeg)。a=cosθ；b=sinθ；c=-sinθ；d=cosθ。

```js
/* 
计算 30° 的sin值：
首先将 30° 转换为弧度，传递给三角函数计算。
用 JS 计算如下： 
*/
// 弧度和角度的转换公式：弧度=π/180×角度 

const radian = Math.PI / 180 * 30 // 算出弧度

const sin = Math.sin(radian) // 计算 sinθ
const cos = Math.cos(radian) // 计算 cosθ

console.log(sin, cos) // 输出 ≈ 0.5, 0.866




```

```css
/*
算出了 sin 和 cos，分别是 0.5 和 0.866
如果我们不考虑缩放和偏移，只旋转30°，矩阵应该表示为
*/
transform: rotate(30deg)

a=0.866

b=0.5

c=-0.5

d=0.866

transform: matrix(0.866, 0.5, -0.5, 0.866, 0, 0);


```


> 博客地址 https://fanmingfei.com/posts/CSS3_Transform_Matrix_Intro.html


