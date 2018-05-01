# Besti_Code_Pattern
# 文件夹/文件 命名规范(试用)
- 所有文件夹按照算法所属分类命名 </br>
- 所有文件按照该文件内代码所实现的算法名加复杂度命名(一个文件只实现一个算法) </br>
- 所有文件均不得出现中文字符. 用下划线('_')代替空格(' '） </br>
eg: </br>
Floder:`图论` </br>
File:  `KMP(m+n).c` </br>

> 树  
>> 二叉树  
>>> 红黑树
>>> ...

> 图论
>> 最短路径
>> ...


----------


# 函数模板编写规范(试用)
- 所有函数名用所实现的算法命名 </br>
- 代码前要用注释说明该函数所实现的功能、复杂度、参数表、与返回值</br>
eg:</br>
<pre><code>
/******************************************
algorthm: Miller–Rabin primality test
input:    long long int p
return:   bool          isprime(1: prime, 0:not prime)
******************************************/
// 18位素数：154590409516822759  
// 19位素数：2305843009213693951 (梅森素数)  
// 19位素数：4384957924686954497  
LL prime[6] = {2, 3, 5, 233, 331};  
LL qmul(LL x, LL y, LL mod) { // 乘法防止溢出， 如果p * p不爆LL的话可以直接乘； O(1)乘法或者转化成二进制加法  
    return (x * y - (long long)(x / (long double)mod * y + 1e-3) *mod + mod) % mod;  
    /* 
    LL ret = 0; 
    while(y) { 
        if(y & 1) 
            ret = (ret + x) % mod; 
        x = x * 2 % mod; 
        y >>= 1; 
    } 
    return ret; 
    */  
}  
LL qpow(LL a, LL n, LL mod) {  
    LL ret = 1;  
    while(n) {  
        if(n & 1) ret = qmul(ret, a, mod);  
        a = qmul(a, a, mod);  
        n >>= 1;  
    }  
    return ret;  
}  
bool Miller_Rabin(LL p) {  
    if(p < 2) return 0;  
    if(p != 2 && p % 2 == 0) return 0;  
    LL s = p - 1;  
    while(! (s & 1)) s >>= 1;  
    for(int i = 0; i < 5; ++i) {  
        if(p == prime[i]) return 1;  
        LL t = s, m = qpow(prime[i], s, p);  
        while(t != p - 1 && m != 1 && m != p - 1) {  
            m = qmul(m, m, p);  
            t <<= 1;  
        }  
        if(m != p - 1 && !(t & 1)) return 0;  
    }  
    return 1;  
}  
</code></pre>


## 图论算法
- 尽量Push能在使用链式前向星所建的图上跑的代码

## ...
- ...


----------
