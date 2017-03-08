# 常用jQuery API

标签（空格分隔）： jQuery

---
具体参考[jQuery API 3.1中文文档][1]
### jQuery
>*   给元素添加事件或方法，如果是没有找到元素，也不会报错，因为jq就是一个对象
判断是否获取到元素，用length 

>*   无new的实例化，让另一个函init作为构造函数。
>*   访问jQuery原型上的方法，需要init.prototype和jQuery.prototype引用同一个对象。


----------


>*  $(document).ready(fn)
当DOM载入就绪可以查询及操纵时绑定一个要执行的函数。
这是事件模块中最重要的一个函数，因为它可以极大地提高web应用程序的响应速度。


```
$(document).ready(function (){
    var inputs = document.getElementsByTagName("input");	
    console.log( inputs );
});
```


------
### jQuery对象

想要使用jq下的方法，需要将其包装成对象形式
$(  ).方法

```
$(function(){
   // var inps = $("input");//用jq获取元素的方法
   var arr = ["q","r",3,5];
    $(arr).each(function( index,item ){
        console.log( index,item );
    })
})
```
------
##1.    jQuery方法
###1.1 $(A).html(value)  
此函数返回一个HTML字符串
取得第一个匹配元素的html内容。这个函数不能用于XML文档。但可以用于XHTML文档
在一个 HTML 文档中, 我们可以使用 .html() 方法来获取任意一个元素的内容。 如果选择器匹配多于一个的元素，那么只有第一个匹配元素的 HTML 内容会被获取。
注意：
参数为结构时， 会被解析

------

###1.2 $(A).text()  此函数返回一个字符串
没有参数表示 取得所有匹配元素的内容。
结果是由所有匹配元素包含的文本内容组合起来的文本。这个方法对HTML和XML文档都有效。
接受两个参数，index为元素在集合中的索引位置，text为原先的text值
>* 参数为结构时， 不会被解析，保留参数内容


------

###1.3 $(A).attr( key，value )  参数有2个
表示在行间 添加 自定义属性。

###1.4 例如 $(A).attr( key )  参数只有一个
表示 获取 在行间添加的自定义属性。

###1.5 $(A).data( key，value ) 
在元素上存放数据,返回jQuery对象。

------

###1.6 $(A).eq( index )   
    获取指定元素，返回值是jq对象
index表示 元素的位置，如果是负数表示从后往前找

------

###1.7 $(A).css( attrName，value )   
    给某个元素添加样式
如果想要批量设置样式，那就传入一个对象格式
```
//传入一个样式
$(A).css( "font-size","20px" )
//传入多组样式，用对象
$(A).css( {
    background:"red",
    "font-size":"20px"
} )   
```
------

###1.8 $(A).addClass( index，className )   
给某个元素添加className

###1.9 $(A).removeClass(className)   
删除某个元素身上的className

------

###1.10 $(A).index( )   

    搜索匹配的元素，并返回相应元素的索引值，从0开始计数。
a. 如果不给 .index()方法传递参数，那么返回值就是这个jQuery对象集合中第一个元素相对于其同辈元素的位置
b. 如果参数是一组DOM元素或者jQuery对象，那么返回值就是传递的元素相对于原先集合的位置 
c. 如果参数是一个选择器，那么返回值就是原先元素相对于选择器匹配元素中的位置。如果找不到匹配的元素，则返回-1   


------

###1.11 $(A).hide( [speed,[easing],[fn]] )
    隐藏显示的元素
a.没有参数时，表示就是直接隐藏，没有动画效果
b.speed表示运动时间，可以是关键词（"slow（600ms）","normal（400ms）", or "fast（200ms）"），也可以是动画时长的毫秒数值（例如：600）

------

###1.12 $(A).toggleClass(class|fn[,sw])
    如果存在（不存在）就删除（添加）一个类。

------
###1.13 jQuery.jQuery(html,[ownerDocument])


------

###1.14  $( A ).each(callback)
    对于每个匹配的元素所要执行的回调函数。
```
// 如果你想得到 jQuery对象，可以使用 $(this) 函数。

$("ul li").each(function( index,item ){
    //每次执行传递进来的函数时，函数中的this关键字都指向一个不同的DOM元素(每次都是一个不同的匹配元素)
    //item == this;
    $(item).attr("index",index);//给每一个li添加自定义属性index
    
})
```

------

###1.15  $( A ).insertbefore( B )   
A和B是兄弟关系
   使用这个方法是把A插入到B前;
    
###1.16  $( A ).before( str | element | jq | fn ) 
在A元素之前插入内容( String, Element, jQuery )
fn函数必须返回一个html字符串。

```

```

------


###1.17 $( A ).remove（[expr] )
  **expr**---用于筛选元素的jQuery表达式，是string类型
从DOM中删除所有匹配的元素。
这个方法不会把匹配的元素从jQuery对象中删除，因而可以在将来再使用这些匹配的元素。但除了这个元素本身得以保留之外，其他的比如绑定的事件，附加的数据等都会被移除。

```
//需求:
//从DOM中把带有hello类的段落删除

//HTML 代码:
<p class="hello">Hello</p> how are <p>you?</p>

//jQuery 代码:
$("p").remove(".hello");
//删除所有p标签中，有class为hello的p标签

//结果:
how are <p>you?</p>

```

----------

###1.18  $( A ).detash([expr])
删除之后，会保留删除元素的事件和保存的数据

----------

###1.20  $( A ).parents([expr])，返回值是集合
取得一个包含着所有匹配元素的祖先元素的元素集合（不包含根元素）。可以通过一个可选的表达式进行筛选。
expr----用于筛选祖先元素的表达式

```
 $( A ).parents()；
//没有参数，表示找到A的所有父级

 $( A ).parents(B)；
//参数B，表示找到A的所有父级中是B的元素集合

```

----------

###1.21 $( A ).parent([expr])
取得一个包含着所有匹配元素的唯一父元素的元素集合。


```

```
----------

###1.22  $( A ).prepend([expr])
取得一个包含着所有匹配元素的唯一父元素的元素集合。


```

```
----------

###1.23  $(  ).val([val|fn|arr])     返回值:String,Array
    获得匹配元素的当前值。

fn是回调函数，要return出来值                                                              
```

```

----------

###1.24   $( A ).clone（blean1[，blean2]）
    克隆匹配的DOM元素并且选中这些克隆的副本。
如果参数是一个布尔值（true 或者 false）指示事件处理函数是否会被复制
默认值是：false
如果参数是两个的时候：
blean1: 一个布尔值（true 或者 false）指示事件处理函数是否会被复制。
blean2: 一个布尔值，指示是否对事件处理程序和克隆的元素的所有子元素的数据应该被复制。


----------

###1.25    $( A ).filter(expr|obj|ele|fn)
    筛选出与 指定表达式 匹配的元素集合。
    
>    参数：
    expr--------------------字符串值，包含供匹配当前元素集合的选择器表达式
    jQuery obj-------------现有的jQuery对象，以匹配当前的元素
    element --------------一个用于匹配元素的DOM元素
    function(index){}----- 一个函数用来作为测试元素的集合。它接受一个参数index，这是元素在jQuery集合的索引。在函数， this指的是当前的DOM元素。



----------

##2. 链式调用
```
var str = "abcd";
str.split("").reverse().join("");//这种是链式调用

//例2：
//模拟jq的编写模式
(function(global,factory){
    factory(global);
//此处把window传进去，优化性能，后面的function函数是return出的各种方法，把方法加在jQuery的圆形上
})(window,function (window,noGlobal){

	//分析整体架构

	var jQuery = function (){
		//return new 	jQuery();  //会循环调用

		return new jQuery.fn.init();
	};


	//jQuery.fn是jQuery.prototype的别名
	jQuery.fn = jQuery.prototype = {
		constructor:jQuery,
		each (){
			console.log("我是each");

			return this;	
		},
		html(){
			console.log("我是html");
			return this;
		},
		css(){
			console.log("我是css");
			return this;
		}
	}

	//可以定义另一个函数，作为构造函数

	var init = jQuery.fn.init = function (){
			
	}

	//让init原型和jQuery的原型共同引用一个对象
	init.prototype = jQuery.fn;
	window.jQuery = window.$ = jQuery;
});

//链式调用方法如下：

$().each().html().css();

```
##3. 学习jQuery选择器

###3.1 ：odd
匹配所有索引值为奇数的元素，从 0 开始计数

    例如：$("ele:odd")//这样就可以获取到想要的元素

###3.2 ：event
匹配所有索引值为偶数的元素，从 0 开始计数

    例如：$("ele:event")//这样就可以获取到想要的元素



##4.事件

###4.1    on(events,[selector],[data],fn)

在选择元素上绑定一个或多个事件的事件处理函数

`参数：events,[selector],[data],fn`
**events**一个或多个用空格分隔的事件类型和可选的**命名空间**，如"click"或"keydown.myPlugin" 。
"click.list"，就是自定义事件，要用  **trigger** 方法 触发
`trigger(type,[data])`

**selector**:一个选择器字符串用于过滤器的触发事件的选择器元素的后代。
如果选择的< null或省略，当它到达选定的元素，事件总是触发。

**data**:当一个事件被触发时要传递event.data给事件处理函数。

**fn**:该事件被触发时执行的函数。
false值也可以做一个函数的简写，返回false。

------

###4.2 $().trigger(type,[data],fn)绑定自定义事件

在每一个匹配的元素上触发某类事件

**type**:一个事件对象或者要触发的事件类型

**data**:传递给事件处理函数的附加参数

**fn**：事件发生时运行的函数

-----

###4.3  $(). toggle([speed],[easing],[fn])

用于绑定两个或多个事件处理器函数，以响应被选元素的轮流的 click 事件
如果元素是可见的，切换为隐藏的；如果元素是隐藏的，切换为可见的。

`参数：[speed],[easing],[fn]`

**speed**:  隐藏/显示 效果的速度。默认是 "0"毫秒。可能的值：slow，normal，fast"，分别代表（600ms，400ms，200ms）

**easing**: (Optional) 用来指定切换效果，默认是"swing"，可用参数"linear"

**fn**: 在动画完成时执行的函数，每个元素执行一次。
```

```
-----

###4.4    $().focus()

当元素获得焦点时，触发 focus 事件。
可以通过鼠标点击或者键盘上的TAB导航触发。这将触发所有绑定的focus函数，注意，某些对象不支持focus方法。
***注意***：不能冒泡


`参数：[data],fn`

**data**: focus([Data], fn) 可传入data供函数fn处理。

**fn**:在每一个匹配元素的focus事件中绑定的处理函数。

-----

###4.5    $().focusin()
当元素获得焦点时，触发 focusin 事件。
focusin事件跟focus事件区别在于，他可以在父元素上检测子元素获取焦点的情况。
***注意***：可以冒泡到父级

`参数：[data],fn`

**data**: focus([Data], fn) 可传入data供函数fn处理。

**fn**:在每一个匹配元素的focus事件中绑定的处理函数。

-----

###4.5    $().focusout()

当元素失去焦点时触发 focusout 事件。
focusout事件跟blur事件区别在于，他可以在父元素上检测子元素失去焦点的情况。

参数

`参数：[data],fn`

**data**: focusout([Data], fn) 可传入data供函数fn处理。

**fn**:在每一个匹配元素的focusout事件中绑定的处理函数。

-----

###4.6    $().animate()

animate(params,[speed],[easing],[fn])

>*  判断元素是不是正在动画状态
$(element).is(":animated")-----true;表示是在动画中

>*  停止当前元素的动画状态
$(this).stop(false,true).animate();//当前动画会直接到达末状态


-----

###4.7    $().stop()

停止所有在指定元素上正在运行的动画

`参数：[clearQueue],[jumpToEnd]`

**clearQueue**: 如果设置成true，则清空队列。可以立即结束动画。

**gotoEnd**:    让当前正在执行的动画立即完成，并且重设show和hide的原始样式，调用回调函数等。

-----

###4.8    $().position()

获取匹配元素相对定位父元素的偏移。返回值:Object{top,left}



-----

###4.9    event.pageX()---- event.pageY()

鼠标相对于文档的左边缘的位置。----鼠标相对于文档的顶部边缘的位置。

-----

###4.10     \$(window).width()----$(window).height()

获取页面的宽高


-----

##5. 事件调用
###5.1  事件调用有2种方法
    实例调用：
    $().方法---实例.方法---扩展要在原型上

    jQuery函数调用：
    \$.方法--静态方法--扩展要在$上

实例去调用某一个方法，会去到原型上找
通过函数调用某个方法(静态方法)，会去函数上找

-----
###5.2  jQuery.extend( ) / $.extend( )

用一个或多个其他对象来扩展一个对象，`返回被扩展的对象（目标对象）`。简单而言，就是合并目标对象的。

`参数：[deep], target, object1, [objectN]`

**deep**:  如果是false，则省略不写，表示浅复制， 如果设为true，则递归合并，表示深复制。

**target**: 待修改对象。
它是一个对象，如果附加的对象被传递给这个方法将那么它将接收新的属性，如果它是唯一的参数将扩展jQuery的命名空间。如果不指定target，则给jQuery命名空间本身进行扩展

**object1**:    待合并到第一个对象的对象。

**objectN**:    待合并到第一个对象的对象。

`注意：如果对象中有相同的属性，那么后合并的会覆盖之前的`

```
var obj1 = {
    a:9,
    b:0;
    arr:[1,2,3,4,5]
}
var obj2 = $.extened({},obj1);//表示将obj1的地址复制一份给obj2
obj2 === obj1;//true，两个对象地址是相同的
//如果obj1中arr变化，那么obj2也会变化，因为地址是相同的

```



##6.书写插件的格式

###6.1 匿名函数自执行，把Jquery作为实参传进去，不能写成符号$

###6.2 扩展的方法如何调用

实例调用   扩展到原型上
函数调用    扩展到函数上

```
(function($){
//通过对象扩展的方法，把这个对象上的属性合并到jQuery的原型上$.fn
    $.fn.drag1 = function(){
        console.log("我是扩展的拖拽方法1")
    }；
    $.fn.drag2 = function(){
        console.log("我是扩展的拖拽方法2")
    }；
    $.fn.drag3 = function(){
        console.log("我是扩展的拖拽方3法")
    }；//...(以此类推)

}(jQuery)；

//使用jq的extened方法后，代码变成了：

(function($){//此处$表示形参
    $.fn.extened({
        drag1:function(){
            console.log("我是扩展的拖拽方法1")
        },
        drag2:function(){
            console.log("我是扩展的拖拽方法2")
        },
        drag3:function(){
            console.log("我是扩展的拖拽方法3")
        }
    })
}(jQuery)//此处jQuery表示传入的实参

```


  [1]: http://jquery.cuishifeng.cn/