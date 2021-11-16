# 1. 线性布局 LinearLayout

## 1.1 线性布局的使用

什么是线性布局？

- 所有的子元素都在一条线上

~~~xml
<linearLayout xmlns:android="" 
              android:layout_width="match_parent" 
              android:layout_height="match_parent">
    <button></button>
</linearLayout>
~~~



## 1.2 线性布局摆放的方向

~~~css
Android:orientation="vertical"
~~~

我们可以通过orientation这个属性来修改线性布局子元素的摆放方向

- horizontal：水平
- vertical：垂直



## 1.3 线性布局中的权重

当有些时候，我们需要平均地给子元素宽度或高度

~~~css
/*先填宽度，再设权重*/
Android:layout_width="0dp"
Android:layout_weight="1"
~~~

有时候给子元素成比例的宽高，也可以使用权重

权重计算：我们把所有的数字加起来，占的份儿就是该控件占总的部分。分子/总数。

~~~xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">
    <Button
        android:id="@+id/button1"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_weight="1"
        android:text="Button"
        tools:layout_editor_absoluteX="15dp"
        tools:layout_editor_absoluteY="36dp" />
    <Button
        android:id="@+id/button2"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_weight="1"
        android:text="Button"
        tools:layout_editor_absoluteX="15dp"
        tools:layout_editor_absoluteY="36dp" />
    <Button
        android:id="@+id/button3"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_weight="2"
        android:text="Button"
        tools:layout_editor_absoluteX="15dp"
        tools:layout_editor_absoluteY="36dp" />

</LinearLayout>
~~~





# 2. 相对布局 RelativeLayout

~~~xml
<RelativeLayout ></RelativeLayout>
~~~



## 2.1 相对布局相对于父控件

wrap_content：居中

~~~xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:text="中间"/>

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentRight="true"
        android:text="右上角"/>

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentLeft="true"
        android:text="左上角"/>

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:text="左下角"/>

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_alignParentRight="true"
        android:text="右下角"/>
</RelativeLayout>
~~~

所有的位置都是相对父组件，也就是上一级的组件：

- ` android:layout_centerInParent="true"`：定义为父组件
- `android:layout_alignParentRight="true"`：相对父组件的右边
- `android:layout_alignParentLeft="true"`：相对父组件的左边
- `android:layout_alignParentBottom="true"`：相对父组件的底部

示意图：

![image-20210915205128486](image/image-20210915205128486.png)



## 2.2 相对布局相对于同级组件

~~~xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:id="@+id/center_button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:text="中间"/>

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerVertical="true"
        android:layout_toLeftOf="@id/center_button"
        android:text="在中间的左边"/>

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerVertical="true"
        android:layout_toRightOf="@id/center_button"
        android:text="在中间的右边"/>

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:layout_above="@id/center_button"
        android:text="在中间的顶部"/>

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:layout_below="@id/center_button"
        android:text="在中间的底部"/>
</RelativeLayout>
~~~

定义一个组件，设置其id（注意这里有个 ==+==）和将其位置定义在垂直居中

~~~css
android:id="@+id/center_button"
android:layout_centerInParent="true"
~~~

则其他同级组件相对该组件位置移动

- 垂直&水平方向
    - `android:layout_centerHorizontal="true"`：垂直
    - `android:layout_centerVertical="true"`：水平
- 相对位置
    - `android:layout_toLeftOf="@id/center_button"`：相对左
    - `android:layout_toRightOf="@id/center_button"`：相对右
    - ` android:layout_above="@id/center_button"`：相对顶部
    - ` android:layout_below="@id/center_button"`：相对底部



示意图：

![image-20210915210613168](image/image-20210915210613168.png)



# 3. 其他布局

## 3.1 绝对布局 AbsoluteLayout

建立平面坐标系来控制，现在已经过时了的

~~~xml
<?xml version="1.0" encoding="utf-8"?>
<AbsoluteLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="next button"
        android:id="@+id/button2"
        android:layout_x="92dp"
        android:layout_y="117dp"/>
</AbsoluteLayout>
~~~

使用对象

- 机顶盒
- 手表

优点：和UI直接图标是一样的

![image-20210915223627234](image/image-20210915223627234.png)



## 3.2 表格布局 TableLayout

`<tablerow></tablerow>`：表示表格中的行

~~~xml
<?xml version="1.0" encoding="utf-8"?>
<TableLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TableRow>
        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="1"/>

        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="2"/>

        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="3"/>
    </TableRow>
    <TableRow>
        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="4"/>

        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="5"/>

        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="6"/>
    </TableRow>
    <TableRow>
        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="7"/>

        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="8"/>

        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="9"/>
    </TableRow>
</TableLayout>
~~~





## 3.3 帧布局 FrameLayout

播放器之类的架构



# 4. 布局中常用的单位

## 4.1 适配单位 dp



## 4.2 像素单位 px



## 4.3 字体单位 sp



# 5. 练习

## 5.1 计算机





# 6. 布局的嵌套使用

 