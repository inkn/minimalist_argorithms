# minimalist_argorithms

> 一些简单算法题的极简写法，方便熟悉 JavaScript 。

## [宝石与石头](https://leetcode-cn.com/problems/length-of-last-word/)

给定字符串 J 代表石头中宝石的类型，和字符串 S 代表你拥有的石头。 S 中每个字符代表了一种你拥有的石头的类型，你想知道你拥有的石头中有多少是宝石。

J 中的字母不重复，J 和 S 中的所有字符都是字母。字母区分大小写，因此 "a" 和 "A" 是不同类型的石头。

示例:
    
```
输入: J = "aA", S = "aAAbbbb"
输出: 3
        
输入: J = "z", S = "ZZ"
输出: 0
```
注意：
- S 和 J 最多含有50个字母。
- J 中的字符不重复。
    
解法：
    
```javascript
var numJewelsInStones = function(J, S) {
    return S.split('').filter( i => J.includes(i)).length
}
```
思路：
1. 将 S 转换成数组
2. 过滤掉数组中不在 J 中的元素
3. 输出最后得到的数组的长度
    
## [转换成小写字母](https://leetcode-cn.com/problems/to-lower-case/)
    
实现函数 ToLowerCase()，该函数接收一个字符串参数 str，并将该字符串中的大写字母转换成小写字母，之后返回新的字符串。

示例:

```
输入: "Hello"
输出: "hello"
```

解法：

```javascript
var toLowerCase = function(str) {
    return str.split('').map( i => String.fromCharCode(i.charCodeAt()|2**5) ).join('')
}
```

思路：  
所有小写字母的 ASCII 码的二进制第六位（从右向左）都是 1 ，而对应的大写字母第六位为 0 ，其他位都一样。   [ASCII码](https://www.cnblogs.com/stxs/p/8846545.html)  
所以转换为小写，只需字符的 ASCII 码的第六位变为 1 ，即与 0x100000 做或运算。
