### JS中的数学函数Math

Math称为数学函数，但是它属于对象类型的

```javascript
typeof Math =>'object'
```

之所以叫做数学函数，是因为Math这个对象中提供了很多操作数字的方法

### Math中提供的常用方法

**`abs`**：取绝对值

```javascript
Math.abs(10)//=>10
Math.sbs(-10)//=>10
```

**`ceil/floor`**：向上或者向下取整

```javascript
//ceil
Math.ceil(10)//=>10
Math.ceil(10.01)//11
Math.ceil(-10.11)//-10
//floor
Math.floor(10.999)//-10
Math.floor(-10.01)//-11
```

**`round`**：四舍五入

```javascript
//正数
Math.round(10.49)//=>10
Math.round(10.5)//=>11
//负数
Math.round(-10.5)//-10
Math.round(-10.51)//-11
```

**`sqrt`**：开平方

```javascript
Math.sqrt(100)//=>10
Math.sqrt(16)//=>4
```

**`pow`**：取幂(n的m次方)

```javascript
Math.pow(2,10)//=>1024
```

**`max/min`**：取最大值/最小值

```javascript
Math.max(12,23,3,123,123,1,23,1)//=>123
Math.min(12,23,3,123,123,1,23,1)//=>1
```

**`PI`**：获取圆周率(注意没有（）)

```javascript
Math.PI //=>3.141592653589793
```

**`random`**：获取0~1之间的随机小数

```javascript
//获取五个0~1之间随机小数
for(var i = 1; i <= 5; i ++){
console.log(Math.random())
}
/*
0.7190898841318569
0.46001780980470475
0.0032373429306959967
0.30429032116502186
0.3437148457383423
*/
```

`Math.round(Math.random()*(m-n)+n)`：获取n~m之间的随机整数

通过（Math) 可以查看其他属性和方法