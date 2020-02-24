### 获取页面中的DOM元素
document.getElementById
>在整个文档中，通过元素的ID属性值，获取到这个元素对象
>
>getElementById是获取元素的方法，而document限定了获取元素的范围，我门把这个范围称之为：“上下文【context】”
```javascript
1. 通过getElementById获取的元素是一个对象数据类型的值（里面包含了很多内置的属性）
typeof oBox => "object"

2. 分析包含的属性
classNmae：存储的是一个字符串，代表当前元素的的样式类名

id:存储的是当前元素的id值（字符串）

innerHtml：存储当前元素中所有的内容（包含HTML标签）

innerHtml：存储当前元素中所有的文本内容（没有元素标签）

onclick:元素的一个事件属性，基于这个属性，可以给当前元素绑定点击事件
onmouseover:鼠标滑过事件
onmouseout：鼠标离开事件

style：存储在当前元素所有的“行内样式”值（获取和操作的都只能是写在标签上的行内样式，写在样式表中的样式，无法基于这个属性获取到）


获取元素className
<li class="oldclass"></li>
li["className"]==li.className
添加类名
li["className"] ="oldclass newclass"
li["className"] += " newclass"//这里新类名之前一定要加空格
```
[context].getElementsByTagName
> 在指定的上下文中，通过元素的标签名获取一组元素集合
>
>上下文是我们自己来指定的

```javascript
var boxList =
oBox.getElementsByTagNmae("li");

1. 获取的结果是一个元素集合（HTMLCollection）,先它也是对象数据类型的，结构和数组非常相似（数字作为索引，length代表长度），但是不是数组，我们把他叫做“类数组”

boxList[0] 获取当前集合中的第一个LI（通过索引获取到具体的某一个LI即可）
boxList.length 获取集合中的LI的数量

2. 集合中的每一项存储的值又是一个元素对象（对象数据类型，包含很多的内置属性，例如：id/className...）

boxList[1].style.color="red";修改集合中第二个LI的文字颜色
```
