# minimalist_argorithms

> һЩ���㷨��ļ���д����������Ϥ JavaScript ��

## [��ʯ��ʯͷ](https://leetcode-cn.com/problems/length-of-last-word/)

�����ַ��� J ����ʯͷ�б�ʯ�����ͣ����ַ��� S ������ӵ�е�ʯͷ�� S ��ÿ���ַ�������һ����ӵ�е�ʯͷ�����ͣ�����֪����ӵ�е�ʯͷ���ж����Ǳ�ʯ��

J �е���ĸ���ظ���J �� S �е������ַ�������ĸ����ĸ���ִ�Сд����� "a" �� "A" �ǲ�ͬ���͵�ʯͷ��

ʾ��:
    
```
����: J = "aA", S = "aAAbbbb"
���: 3
        
����: J = "z", S = "ZZ"
���: 0
```
ע�⣺
- S �� J ��ຬ��50����ĸ��
- J �е��ַ����ظ���
    
�ⷨ��
    
```javascript
var numJewelsInStones = function(J, S) {
    return S.split('').filter( i => J.includes(i)).length
}
```
˼·��
1. �� S ת��������
2. ���˵������в��� J �е�Ԫ��
3. ������õ�������ĳ���
    
## [ת����Сд��ĸ](https://leetcode-cn.com/problems/to-lower-case/)
    
ʵ�ֺ��� ToLowerCase()���ú�������һ���ַ������� str���������ַ����еĴ�д��ĸת����Сд��ĸ��֮�󷵻��µ��ַ�����

ʾ��:

```
����: "Hello"
���: "hello"
```

�ⷨ��

```javascript
var toLowerCase = function(str) {
    return str.split('').map( i => String.fromCharCode(i.charCodeAt()|2**5) ).join('')
}
```

˼·��  
����Сд��ĸ�� ASCII ��Ķ����Ƶ���λ���������󣩶��� 1 ������Ӧ�Ĵ�д��ĸ����λΪ 0 ������λ��һ����   [ASCII��](https://www.cnblogs.com/stxs/p/8846545.html)  
����ת��ΪСд��ֻ���ַ��� ASCII ��ĵ���λ��Ϊ 1 ������ 0x100000 �������㡣
