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
    return str.split('').map( i => String.fromCharCode(i.charCodeAt() | 2**5) ).join('')
}
```

思路：  
所有小写字母的 ASCII 码的二进制第六位（从右向左）都是 1 ，而对应的大写字母第六位为 0 ，其他位都一样。   [ASCII码表](https://www.cnblogs.com/stxs/p/8846545.html)  
所以转换为小写，只需字符的 ASCII 码的第六位变为 1 ，即与 0x100000 做或运算。

## [翻转图像](https://leetcode-cn.com/problems/flipping-an-image/)

给定一个二进制矩阵 A，我们想先水平翻转图像，然后反转图像并返回结果。

水平翻转图片就是将图片的每一行都进行翻转，即逆序。例如，水平翻转 [1, 1, 0] 的结果是 [0, 1, 1]。

反转图片的意思是图片中的 0 全部被 1 替换， 1 全部被 0 替换。例如，反转 [0, 1, 1] 的结果是 [1, 0, 0]。


示例:

```
输入: [[1,1,0],[1,0,1],[0,0,0]]
输出: [[1,0,0],[0,1,0],[1,1,1]]
解释: 首先翻转每一行: [[0,1,1],[1,0,1],[0,0,0]]；
     然后反转图片: [[1,0,0],[0,1,0],[1,1,1]]
```

解法：

```javascript
var flipAndInvertImage = function(A) {
    return A.map(arr => arr.reverse().map( i => i ^ 1))
}
```

思路：  

1 => 0 :  `1 ^ 1 = 0`  
0 => 1 : `0 ^ 1 = 1` 

## [唯一摩尔斯密码词](https://leetcode-cn.com/problems/unique-morse-code-words/)

国际摩尔斯密码定义一种标准编码方式，将每个字母对应于一个由一系列点和短线组成的字符串， 比如: "a" 对应 ".-", "b" 对应 "-...", "c" 对应 "-.-.", 等等。

为了方便，所有26个英文字母对应摩尔斯密码表如下：
```
[".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]
```
给定一个单词列表，每个单词可以写成每个字母对应摩尔斯密码的组合。例如，"cab" 可以写成 "-.-..--..."，(即 "-.-." + "-..." + ".-"字符串的结合)。我们将这样一个连接过程称作单词翻译。

返回我们可以获得所有词不同单词翻译的数量。

示例:

```
例如:
输入: words = ["gin", "zen", "gig", "msg"]
输出: 2
解释: 
各单词翻译如下:
"gin" -> "--...-."
"zen" -> "--...-."
"gig" -> "--...--."
"msg" -> "--...--."

共有 2 种不同翻译, "--...-." 和 "--...--.".
```
注意:

- 单词列表words 的长度不会超过 100。
- 每个单词 words[i]的长度范围为 [1, 12]。
- 每个单词 words[i]只包含小写字母。

解法：

```javascript
var mosList = [".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]

var uniqueMorseRepresentations = function(words) {
    return [...new Set(words.map(i => i.split('').reduce((acc,current) => acc + mosList[current.charCodeAt() - 97], '')))].length
};
```

思路：

1. 先把数组 words 里的字符串翻译成摩斯密码   
> 字符串 --- split('') ---> 数组 --- reduce( 将每个字符对应的莫斯字符累加起来 ) ---> 翻译后的字符串  

2. 然后对这个数组去重返回长度
```
var a = [1, 2, 3, 2, 1]
a = [...new Set(a)]  // [1, 2, 3]

// Set 集合中的值是唯一的，不能重复
// 所以先用数组初始化一个 Set 集合去掉重复元素
// 然后使用扩展运算符 ... 让 Set 集合转化为数组 
```

## [独特的电子邮件地址](https://leetcode-cn.com/problems/unique-email-addresses/)

每封电子邮件都由一个本地名称和一个域名组成，以 @ 符号分隔。

例如，在 alice@leetcode.com中， alice 是本地名称，而 leetcode.com 是域名。

除了小写字母，这些电子邮件还可能包含 '.' 或 '+'。

如果在电子邮件地址的本地名称部分中的某些字符之间添加句点（'.'），则发往那里的邮件将会转发到本地名称中没有点的同一地址。例如，"alice.z@leetcode.com” 和 “alicez@leetcode.com” 会转发到同一电子邮件地址。 （请注意，此规则不适用于域名。）

如果在本地名称中添加加号（'+'），则会忽略第一个加号后面的所有内容。这允许过滤某些电子邮件，例如 m.y+name@email.com 将转发到 my@email.com。 （同样，此规则不适用于域名。）

可以同时使用这两个规则。

给定电子邮件列表 emails，我们会向列表中的每个地址发送一封电子邮件。实际收到邮件的不同地址有多少？

 

示例：
```
输入：["test.email+alex@leetcode.com","test.e.mail+bob.cathy@leetcode.com","testemail+david@lee.tcode.com"]
输出：2
解释：实际收到邮件的是 "testemail@leetcode.com" 和 "testemail@lee.tcode.com"。
``` 

提示：

- 1 <= emails[i].length <= 100
- 1 <= emails.length <= 100
- 每封 emails[i] 都包含有且仅有一个 '@' 字符。

解法：

```javascript
var numUniqueEmails = function(emails) {
    return [...new Set( emails.map(e => e.split('@')[0].split('.').join('').split('+')[0] + '@' + e.split('@')[1]))].length    
}
```

思路：

1. map 遍历处理每个邮箱
2. 根据 '@' 分割邮箱的本地名称和域名
3. 对本地名称按照规则处理
```javascript
var domain = e.split('@')[1]
var name = e.split('@')[0]
name = name.split('.').join('')  // 忽略 .
name = name.split('+')[0]  // 忽略 + 后面的字符
return name + '@' + domain

// 合并一下：
e.split('@')[0].split('.').join('').split('+')[0] + '@' + e.split('@')[1]
```
4. 对处理完所有的邮箱的数组去重返回长度

---
未完待续...