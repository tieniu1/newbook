### tab切换
>思路:  
>1. 给所有li绑定点击事件，当点击任何一个LI的时候，都做第二步操作  
>2. 可以先让所有的LI和相对应的DIV有ACTIVE这个样式即可

>事件绑定：给当前元素的某一个事件绑定一个方法，绑定的时候方法没有执行（属于创建一个方法），挡在页面种手动出发点击事件的时候绑定的方法才会执行

#### 自定义属性方法
```javascript
// 获取元素
 var oBox = document.querySelector("#box");
    var oLi = document.querySelectorAll("li");
    var oDiv = oBox.querySelectorAll("div");
    for (var i = 0; i < oLi.length; i++) {
        // 给所有的LI添加自定义属性index，用来存储索引
        oLi[i].index = i;
        oLi[i].onclick = function () {
changetab(i)//->此处的i不是当前点击的这个里的索引（原因：绑定方法的时候，方法还没有执行，存储的是字符串"changetaba(i)",单循环结束【i=3】,我们手动去操作LI的时候，方法才会执行，此时changeTab(i)中的变量i已经是循环后的3了）



            // 把当前的索引传给changetab()
            changetab(this.index)
        }
    }

    function changetab(index) {
        // 先给元素清空样式
        for (var i = 0; i < oLi.length; i++) {
            oLi[i].className =oDiv[i].className = "";
        }
        // 给当前元素添加样式类名
        oLi[index].className =oDiv[index].className = "active";
        ;
    }
```
### lastindex
```javascript
  
    var lastIndex = 0;//=>本意记录最后依次选项卡选中的缩影（开始默认第一个被选中，所以lastIndex出事值为0）最后依次价于当前点击的上一次
/*假设我点击了第二个
1. 先把上一次的清空（不需要清空所有）=》lastIndex索引存储的值就是上一次选中的LI的索引
oLi[last_index].className = oDiv[last_index].className = "";
2. 当前点击的是谁，让那个谁有选中的样式（一人需要给每一个LI设置一个自定义属性存储他的索引 index）
this.className = oDiv[this.index].className = "active";
3. 当前本次选中的这一项，其实就是上一次点击要清除的上一项
last_index = this.index

*/ 
    for (var i = 0; i < oLi.length; i++) {
        oLi[i].index = i;
        oLi[i].onclick = function () {
            // 点击的时候让那个上一次被选中的清除样式类名
            oLi[last_index].className = oDiv[last_index].className = "";
            this.className = oDiv[this.index].className = "active";
            last_index = this.index
        }
    }

```
### 传递对象
> 点击把自身传递出去
```javascript
   for (var i = 0; i < oLi.length; i++) {
        oLi[i].onclick = function () {
            changetab(this)//将自身传递出去
        }
    }

    function changetab(item) {
        for (var i = 0; i < oLi.length; i++) {
            //将oli每一项和传进来的li对比,如果是传进来则添加active类名，然后进行下次循环
            if (oLi[i] === item) {
                oLi[i].className = oDiv[i].className = "active";
                continue;
            }
            // 不是当前点击的则清空类名
        oLi[i].className = oDiv[i].className = "";

        }
    }
```
### let方法
>只需要把添加点击事件的循环的var 改为let
```javascript
  for (let i = 0; i < oLi.length; i++) {
        oLi[i].onclick = function () {
            changetab(i)
        }
    }

    function changetab(index) {
        for (var i = 0; i < oLi.length; i++) {
            oLi[i].className = "";
            oDiv[i].className = "";
        }
        oLi[index].className = "active";
        oDiv[index].className = "active";
    }
```
### 闭包
```javascript
 for (var i = 0; i < oLi.length; i++) {
        function(){
             oLi[i].onclick = function () {
            // 把当前的索引传给changetab()
            changetab(this.index)
  }          
   }             
    }
```
### 又一种
```javascript
 for (var i = 0; i < oLi.length; i++) {
        oLi[i].onclick = function (i) {
           return function(){
            changetab(i)
            }
  }          
    }
```
