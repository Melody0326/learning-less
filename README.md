# learning-less
## less的学习笔记

LESS 将 CSS 赋予了动态语言的特性，如 变量， 继承， 运算， 函数。

[less官方中文网站](http://lesscss.cn/)  

[less在线编译器](http://tool.oschina.net/less)  

[less编译工具-Koala](http://koala-app.com/)  


###less常用语法
* 变量
 
* 混合

* 带参数混合

* @arguments 变量

* 嵌套规则

* 命名空间

* 作用域


```
@charset"utf-8";

 注释的区别
/*我是被编译的*/
//不会被编译的

 //less中的变量, 用@声明
@test_width: 300px;
.box{
  width: @test_width;
  height: @test_width;
  background: yellow;
  .border;
}

 //混合
.border{
  border: 5px solid pink;
}

.box2{
  .box;
  margin-left: 100px;
}

 //混合-可带参数
.border_02(@border_width){
  border: @border_width solid yellow;
}

.test_hunhe{
  .border_02(30px);
}

.border_03(@border_width: 10px){
  border: @border_width solid green;
}

.test_hunhe03{
  .border_03();
}

 //混合的例子
.border_radius(@raidus:5px){
  border-radius: @raidus;
  -webkit-border-radius: @raidus;
  -moz-border-radius: @raidus;
}
.radius_test{
  width: 100px;
  height: 40px;
  background: green;
  .border_radius(10px);
}
//.sanjiao{
//  width: 0;
//  height: 0;
//  overflow: hidden;
//
//  border-width: 10px;
//  border-color: transparent transparent red transparent;
//  border-style: dashed dashed solid dashed;
//}

 //匹配模式
.triangle(top,@w:5px,@c:#ccc){
  border-width: @w;
  border-color: transparent transparent @c transparent;
  border-style: dashed dashed solid dashed;
}
.triangle(bottom,@w:5px,@c:#ccc){
  border-width: @w;
  border-color: @c transparent transparent transparent;
  border-style: solid dashed dashed dashed;
}
.triangle(left,@w:5px,@c:#ccc){
  border-width: @w;
  border-color: transparent  @c transparent transparent;
  border-style: dashed solid dashed dashed;
}
.triangle(right,@w:5px,@c:#ccc){
  border-width: @w;
  border-color: transparent transparent transparent @c;
  border-style: dashed dashed dashed solid;
}
.triangle(@_,@w:5px,@c:#ccc){
  width: 0;
  height: 0;
  overflow: hidden;
}

.sanjiao{
  .triangle(top,100px);
}

 //匹配模式-定位例子
.pos(r){
  position: relative;
}
.pos(a){
  position: absolute;
}
.pos(f){
  position: fixed;
}

.pipei{
  width: 200px;
  height: 200px;
  background: green;
  .pos(r);
}

@test_01:300px;
.box_02{
  width:@test_01 + 20;
  //color: #cccccc - 10;
}

 //嵌套
/*
.list{}
.list li{}
.list a{}
.list span{}*/

.list{
  width: 600px;
  margin: 30px auto;
  padding: 0;
  list-style: none;

  li{
    height: 30px;
    line-height: 30px;
    background: pink;
    margin-bottom: 5px;
    padding: 0 10px;
  }
  a{
    float: left;
    //&代表她的上一层选择器
    &:hover{
      color: red;
    }
  }
  span{
    float: right;
  }
}

.border_arg(@w:30px,@c:red,@xx:solid){
  border:@arguments;
}

.test_arguments{
  .border_arg(40px);
}

 //避免编译 ~''
.test_03{
  width: ~'calc(300px - 30px)';
}

* //important,尽量不用
.test_important{
  .border_03() !important;
}
```

[更多高级功能，请访问官方网站] (http://lesscss.org/)

