## LeetCode刷题笔记

### 二分查找模板

```cpp
int l,r,mid;
while(l<=r){
    mid = (l+r)/2;
    // 如果符合条件,check返回true
    if(check(mid)) l = mid+1;
    else r = mid-1;
}
return r;
```

关于返回值为`r`的解释: $mid$ 满足条件说明比 $mid$ 小的都满足,因此我们要把 $l$ 右移为`mid+1`去找更大的临界点. 那么 $l$ 最后的位置再减一,就一定是最后符合条件的 $mid$.而这个位置恰巧就是$r$,因为while停止的条件是 `r<l` ,即 `r=l-1=mid`, 故返回 r.

### JavaScript相关

#### 实现整数除法

JS中的除法运算默认返回的是小数,要想得到类似C++中int类型相除的结果，需要利用一些额外的取整方法.

| 语法           | 描述         |
| -------------- | ------------ |
| `Math.floor()` | 向下取整     |
| `Math.ceil()`  | 向上取整     |
| `Math.round()` | 四舍五入取整 |
| `parseInt()`   | 舍弃小数部分 |

#### 数组初始化

```js
var qwq = new Array(5).fill(7); // [7,7,7,7,7]
var qwq = [2,3,4,5]; // [2,3,4,5]
var qwq = new Array(1,2,3); // [1,2,3]
```

#### 字符与数字转换

+ 字符转数字: 借助`charCodeAt`函数.语法规范: `stringObject.charCodeAt(index)`返回 index 处字符的Unicode编码.

```js
let s = "abcdefg";
let pos0 = s.charCodeAt(0)-'a'.charCodeAt(0);  // 'a' -> 1
let pos1 = s.charCodeAt(1)-'a'.charCodeAt(0);  // 'b' -> 2
```

+ 数字转字符: 借助`fromCharCode`函数.语法规范:`String.fromCharCode(num)`返回Unicode编码nun对应的字符.

```js
let s = "abd";
s += String.fromCharCode(2+'a'.charChodeAt(0)); // s = "abdc"
```

#### replace回调函数

`replace`方法的第一个参数为正则表达式,第二个参数通常为想要替换成的文本,事实上第二个参数也可以是一个函数.

1. 函数的第一个参数为匹配成功的字符串.

2. 函数的后面几个参数分别代表子匹配.

3. **函数的返回值为替换文本**,即第一个参数的字符串变为函数的返回值

```js
var s = "2023-01-15";
const reg = /(\d{4})-(\d{2})-(\d{2})/;
let ans = s.replace(reg, function (word, p1, p2, p3) {
    console.log(word, p1, p2, p3);
    return "#";
});
// word: 2023-01-15
// p1: 2023 p2: 01 p3: 15
// 替换后: # 
```



