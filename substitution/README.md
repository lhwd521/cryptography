###
###    Date:2018-08-11
###   Time:03:33 GMT
###  Author:nianhua
###

````
Python 3.6.6 (default, Jun 27 2018, 14:44:17) 
Type "copyright", "credits" or "license" for more information.

In [1]: from NHstitution import *

In [2]: newobj = SimSubst()

In [3]: print(newobj.encode("nianhua"))
foqfixq

In [4]: print(newobj.uncode("foqfixq"))
nianhua

````
简单替换密码的破解：</br>
  对于简单替代密码的破解，大致可分为以下三类方法：<br>
  * 暴力破解：在密钥空间较小的情况下可以使用穷举法
  * 频率统计：在密钥长度足够的时候可以使用频率统计分析方法，可以参照维吉尼亚的破解
  * 爬山法  ：选择性的尝试不同的密钥，然后给每个解密出来的明文标记一个适应度。若解密出来的明文越接近我们
              平时使用的英文，则他的适应度越高；反之则适应度越低。
  
在学习爬山算法之前，首先要了解Quadgram适应度统计</br>
&nbsp;&nbsp;我们需要的是一种能够确定一段文字与英语相似与否的方法。这可以通过计算'quadgrams'来实现。
&nbsp;&nbsp;例如英文文本ATTACK中的四元组是ATTA\TTAC\TACK
&nbsp;%nbsp;**需要注意的是单个字母的频率、二元组和三元组也可以用于此目的**
我的经验表明，四元组频率的工作效果略好于三元组，三元组的工作效果略好于二元组等，当高于四元组时并不会产生任何好处。
例如我们计算托尔斯泰“战争与和平”中的四元组，在删除所有空格和标点符号后，我们总共有大约2,500,000个四元组。
通过将该四元组的计数除以训练语料库中的四元组总数来计算特定四元组的概率。对数概率只是该数字的对数。一些特定的计数：





