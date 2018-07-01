##打印日志的方式不能太直观理解红黄树算法， 参考了网上的代码和easejs文档，完成了一个前端网页的的动态展示红黑树算法的一个html文件，需要联网使用~因为依赖 easejs cdn


## 时间复杂度的证明
 估计有很多人对书上13.1 引理不是很在意，但是我想说，这正是理解红黑树精髓的地方之一。 这条引理也是红黑树为什么效率这么高的原因。不晓得是语文差还是啥的，我看书上的介绍也没看懂，写得太简洁了，菜鸟看不懂表示很蛋疼。后来在网上看了别人的资料，终于弄懂了。(⊙o⊙)…
下面我就仔仔细细的介绍下这条引理到底是怎么得到的。
引理：一棵有n个内结点的红黑树的高度至多为2lg(n+1)。
这个引理怎么证明呢，这里需要一个工具  对以x为根的子树，它所包含的内部结点数至少为2^[bh(x)]-1。这里bh(x)（bh嘛，black height）被定义为结点x的黑高度，就是说，从结点x（不包括它本身）到它任一个叶结点的路径上所有黑色结点的个数。
下面用归纳法证明：
1)若x高度为0，那么它就是一叶子结点，它确实至少包含2^0-1=0个内部结点
2)假设x为红黑树的某一内部结点，且它高度h>0，那么它的黑高度就是bh(x)，但是它的两个孩子结点呢？这个就根据它们的颜色来判断了：
如果x有一个红色的孩子y，那么y的黑高度bh(y)=bh(x)，看看上面对黑高度的定义你就明白了——既然它是红色的，那么它的黑高度就应该和它父亲的黑高度是一样的；
如果x有一个黑色的孩子z，那么z的黑高度bh(z)=bh(x)-1，这个怎么解释呢，因为它自己就是个黑结点，那么在计算它的黑高度时，必须把它自己排除在外（还是根据定义），所以它是bh(x)-1。
3)x的孩子结点所构成的子树的高度肯定小于x这颗子树，那么对于这两个孩子，不管它们颜色如何，一定满足归纳假设的是至少hb 高度为bh(x)-1。所以，对x来说，它所包含的内部结点个数“至少”为两个孩子结点所包含的内部结点数，再加上它自己，于是就为2^[bh(x)-1]-1+2^[bh(x)-1]-1+1=2^[bh(x)]-1，归纳证明完毕。
也就是说n>=2^[bh(x)]-1---------①
把一 中红黑树性质中 4）、5）两个特性结合起来，其实我们可以得到黑节点至少是红节点的2倍。用一句话来说就是“有红必有黑，但有黑未必一定有红”。为什么这么说呢，因为从特性4）我们知道，如果有一个红结点存在，那么它的儿子结点一定是黑的，最极端的情况下，该路径上所有的结点就被红、黑两种结点给平分了那就是黑节点至少是红节点的2倍。不知这个问题我解释清楚没有，因为这是往下理解的关键。
如果一棵红黑树的高为h，那么在这个高度上（不包括根结点本身）至少有1/2h的黑结点，再结合上面对“黑高度”的定义，我们说，红黑树根结点的黑高度至少是1/2h，好了，我们拿出公式①，设n为该红黑树所包含的内部结点数，我们得出如下结论： n>=2^(1/2h)-1。 我们把它整理整理，就得到了h<=2lg(n+1)，就是我们要证明的结论：红黑树的高度最多也就是2lg(n+1)。
   时间复杂度的底都是相对的所以不说具体对数的底是多少
# RBTree
红黑树算法的完整实现，
日志如下：

== 原始数据: 10 40 30 60 90 70 20 50 80 123 12 34 45 56 67 213 214 344 
== 添加节点: 10
== 树的详细信息: 
10(B) is root

== 添加节点: 40
== 树的详细信息: 
10(B) is root
40(红) is 10'的儿子  right child  父亲是     10

== 添加节点: 30
== 树的详细信息: 
30(B) is root
10(红) is 30'的儿子   left child  父亲是     30
40(红) is 30'的儿子  right child  父亲是     30

== 添加节点: 60
== 树的详细信息: 
30(B) is root
10(黑) is 30'的儿子   left child  父亲是     30
40(黑) is 30'的儿子  right child  父亲是     30
60(红) is 40'的儿子  right child  父亲是     40

== 添加节点: 90
== 树的详细信息: 
30(B) is root
10(黑) is 30'的儿子   left child  父亲是     30
60(黑) is 30'的儿子  right child  父亲是     30
40(红) is 60'的儿子   left child  父亲是     60
90(红) is 60'的儿子  right child  父亲是     60

== 添加节点: 70
== 树的详细信息: 
30(B) is root
10(黑) is 30'的儿子   left child  父亲是     30
60(红) is 30'的儿子  right child  父亲是     30
40(黑) is 60'的儿子   left child  父亲是     60
90(黑) is 60'的儿子  right child  父亲是     60
70(红) is 90'的儿子   left child  父亲是     90

== 添加节点: 20
== 树的详细信息: 
30(B) is root
10(黑) is 30'的儿子   left child  父亲是     30
20(红) is 10'的儿子  right child  父亲是     10
60(红) is 30'的儿子  right child  父亲是     30
40(黑) is 60'的儿子   left child  父亲是     60
90(黑) is 60'的儿子  right child  父亲是     60
70(红) is 90'的儿子   left child  父亲是     90

== 添加节点: 50
== 树的详细信息: 
30(B) is root
10(黑) is 30'的儿子   left child  父亲是     30
20(红) is 10'的儿子  right child  父亲是     10
60(红) is 30'的儿子  right child  父亲是     30
40(黑) is 60'的儿子   left child  父亲是     60
50(红) is 40'的儿子  right child  父亲是     40
90(黑) is 60'的儿子  right child  父亲是     60
70(红) is 90'的儿子   left child  父亲是     90

== 添加节点: 80
== 树的详细信息: 
30(B) is root
10(黑) is 30'的儿子   left child  父亲是     30
20(红) is 10'的儿子  right child  父亲是     10
60(红) is 30'的儿子  right child  父亲是     30
40(黑) is 60'的儿子   left child  父亲是     60
50(红) is 40'的儿子  right child  父亲是     40
80(黑) is 60'的儿子  right child  父亲是     60
70(红) is 80'的儿子   left child  父亲是     80
90(红) is 80'的儿子  right child  父亲是     80

== 添加节点: 123
== 树的详细信息: 
60(B) is root
30(红) is 60'的儿子   left child  父亲是     60
10(黑) is 30'的儿子   left child  父亲是     30
20(红) is 10'的儿子  right child  父亲是     10
40(黑) is 30'的儿子  right child  父亲是     30
50(红) is 40'的儿子  right child  父亲是     40
80(红) is 60'的儿子  right child  父亲是     60
70(黑) is 80'的儿子   left child  父亲是     80
90(黑) is 80'的儿子  right child  父亲是     80
123(红) is 90'的儿子  right child  父亲是     90

== 添加节点: 12
== 树的详细信息: 
60(B) is root
30(红) is 60'的儿子   left child  父亲是     60
12(黑) is 30'的儿子   left child  父亲是     30
10(红) is 12'的儿子   left child  父亲是     12
20(红) is 12'的儿子  right child  父亲是     12
40(黑) is 30'的儿子  right child  父亲是     30
50(红) is 40'的儿子  right child  父亲是     40
80(红) is 60'的儿子  right child  父亲是     60
70(黑) is 80'的儿子   left child  父亲是     80
90(黑) is 80'的儿子  right child  父亲是     80
123(红) is 90'的儿子  right child  父亲是     90

== 添加节点: 34
== 树的详细信息: 
60(B) is root
30(红) is 60'的儿子   left child  父亲是     60
12(黑) is 30'的儿子   left child  父亲是     30
10(红) is 12'的儿子   left child  父亲是     12
20(红) is 12'的儿子  right child  父亲是     12
40(黑) is 30'的儿子  right child  父亲是     30
34(红) is 40'的儿子   left child  父亲是     40
50(红) is 40'的儿子  right child  父亲是     40
80(红) is 60'的儿子  right child  父亲是     60
70(黑) is 80'的儿子   left child  父亲是     80
90(黑) is 80'的儿子  right child  父亲是     80
123(红) is 90'的儿子  right child  父亲是     90

== 添加节点: 45
== 树的详细信息: 
60(B) is root
30(黑) is 60'的儿子   left child  父亲是     60
12(黑) is 30'的儿子   left child  父亲是     30
10(红) is 12'的儿子   left child  父亲是     12
20(红) is 12'的儿子  right child  父亲是     12
40(红) is 30'的儿子  right child  父亲是     30
34(黑) is 40'的儿子   left child  父亲是     40
50(黑) is 40'的儿子  right child  父亲是     40
45(红) is 50'的儿子   left child  父亲是     50
80(黑) is 60'的儿子  right child  父亲是     60
70(黑) is 80'的儿子   left child  父亲是     80
90(黑) is 80'的儿子  right child  父亲是     80
123(红) is 90'的儿子  right child  父亲是     90

== 添加节点: 56
== 树的详细信息: 
60(B) is root
30(黑) is 60'的儿子   left child  父亲是     60
12(黑) is 30'的儿子   left child  父亲是     30
10(红) is 12'的儿子   left child  父亲是     12
20(红) is 12'的儿子  right child  父亲是     12
40(红) is 30'的儿子  right child  父亲是     30
34(黑) is 40'的儿子   left child  父亲是     40
50(黑) is 40'的儿子  right child  父亲是     40
45(红) is 50'的儿子   left child  父亲是     50
56(红) is 50'的儿子  right child  父亲是     50
80(黑) is 60'的儿子  right child  父亲是     60
70(黑) is 80'的儿子   left child  父亲是     80
90(黑) is 80'的儿子  right child  父亲是     80
123(红) is 90'的儿子  right child  父亲是     90

== 添加节点: 67
== 树的详细信息: 
60(B) is root
30(黑) is 60'的儿子   left child  父亲是     60
12(黑) is 30'的儿子   left child  父亲是     30
10(红) is 12'的儿子   left child  父亲是     12
20(红) is 12'的儿子  right child  父亲是     12
40(红) is 30'的儿子  right child  父亲是     30
34(黑) is 40'的儿子   left child  父亲是     40
50(黑) is 40'的儿子  right child  父亲是     40
45(红) is 50'的儿子   left child  父亲是     50
56(红) is 50'的儿子  right child  父亲是     50
80(黑) is 60'的儿子  right child  父亲是     60
70(黑) is 80'的儿子   left child  父亲是     80
67(红) is 70'的儿子   left child  父亲是     70
90(黑) is 80'的儿子  right child  父亲是     80
123(红) is 90'的儿子  right child  父亲是     90

== 添加节点: 213
== 树的详细信息: 
60(B) is root
30(黑) is 60'的儿子   left child  父亲是     60
12(黑) is 30'的儿子   left child  父亲是     30
10(红) is 12'的儿子   left child  父亲是     12
20(红) is 12'的儿子  right child  父亲是     12
40(红) is 30'的儿子  right child  父亲是     30
34(黑) is 40'的儿子   left child  父亲是     40
50(黑) is 40'的儿子  right child  父亲是     40
45(红) is 50'的儿子   left child  父亲是     50
56(红) is 50'的儿子  right child  父亲是     50
80(黑) is 60'的儿子  right child  父亲是     60
70(黑) is 80'的儿子   left child  父亲是     80
67(红) is 70'的儿子   left child  父亲是     70
123(黑) is 80'的儿子  right child  父亲是     80
90(红) is 123'的儿子   left child  父亲是    123
213(红) is 123'的儿子  right child  父亲是    123

== 添加节点: 214
== 树的详细信息: 
60(B) is root
30(黑) is 60'的儿子   left child  父亲是     60
12(黑) is 30'的儿子   left child  父亲是     30
10(红) is 12'的儿子   left child  父亲是     12
20(红) is 12'的儿子  right child  父亲是     12
40(红) is 30'的儿子  right child  父亲是     30
34(黑) is 40'的儿子   left child  父亲是     40
50(黑) is 40'的儿子  right child  父亲是     40
45(红) is 50'的儿子   left child  父亲是     50
56(红) is 50'的儿子  right child  父亲是     50
80(黑) is 60'的儿子  right child  父亲是     60
70(黑) is 80'的儿子   left child  父亲是     80
67(红) is 70'的儿子   left child  父亲是     70
123(红) is 80'的儿子  right child  父亲是     80
90(黑) is 123'的儿子   left child  父亲是    123
213(黑) is 123'的儿子  right child  父亲是    123
214(红) is 213'的儿子  right child  父亲是    213

== 添加节点: 344
== 树的详细信息: 
60(B) is root
30(黑) is 60'的儿子   left child  父亲是     60
12(黑) is 30'的儿子   left child  父亲是     30
10(红) is 12'的儿子   left child  父亲是     12
20(红) is 12'的儿子  right child  父亲是     12
40(红) is 30'的儿子  right child  父亲是     30
34(黑) is 40'的儿子   left child  父亲是     40
50(黑) is 40'的儿子  right child  父亲是     40
45(红) is 50'的儿子   left child  父亲是     50
56(红) is 50'的儿子  right child  父亲是     50
80(黑) is 60'的儿子  right child  父亲是     60
70(黑) is 80'的儿子   left child  父亲是     80
67(红) is 70'的儿子   left child  父亲是     70
123(红) is 80'的儿子  right child  父亲是     80
90(黑) is 123'的儿子   left child  父亲是    123
214(黑) is 123'的儿子  right child  父亲是    123
213(红) is 214'的儿子   left child  父亲是    214
344(红) is 214'的儿子  right child  父亲是    214

== 前序遍历: 60 30 12 10 20 40 34 50 45 56 80 70 67 123 90 214 213 344 
== 中序遍历: 30 12 10 20 40 34 50 45 56 60 80 70 67 123 90 214 213 344 
== 后序遍历: 30 12 10 20 40 34 50 45 56 80 70 67 123 90 214 213 344 60 
== 树的详细信息: 
60(B) is root
30(黑) is 60'的儿子   left child  父亲是     60
12(黑) is 30'的儿子   left child  父亲是     30
10(红) is 12'的儿子   left child  父亲是     12
20(红) is 12'的儿子  right child  父亲是     12
40(红) is 30'的儿子  right child  父亲是     30
34(黑) is 40'的儿子   left child  父亲是     40
50(黑) is 40'的儿子  right child  父亲是     40
45(红) is 50'的儿子   left child  父亲是     50
56(红) is 50'的儿子  right child  父亲是     50
80(黑) is 60'的儿子  right child  父亲是     60
70(黑) is 80'的儿子   left child  父亲是     80
67(红) is 70'的儿子   left child  父亲是     70
123(红) is 80'的儿子  right child  父亲是     80
90(黑) is 123'的儿子   left child  父亲是    123
214(黑) is 123'的儿子  right child  父亲是    123
213(红) is 214'的儿子   left child  父亲是    214
344(红) is 214'的儿子  right child  父亲是    214

== 删除节点: 10
== 树的详细信息: 
60(B) is root
30(黑) is 60'的儿子   left child  父亲是     60
12(黑) is 30'的儿子   left child  父亲是     30
20(红) is 12'的儿子  right child  父亲是     12
40(红) is 30'的儿子  right child  父亲是     30
34(黑) is 40'的儿子   left child  父亲是     40
50(黑) is 40'的儿子  right child  父亲是     40
45(红) is 50'的儿子   left child  父亲是     50
56(红) is 50'的儿子  right child  父亲是     50
80(黑) is 60'的儿子  right child  父亲是     60
70(黑) is 80'的儿子   left child  父亲是     80
67(红) is 70'的儿子   left child  父亲是     70
123(红) is 80'的儿子  right child  父亲是     80
90(黑) is 123'的儿子   left child  父亲是    123
214(黑) is 123'的儿子  right child  父亲是    123
213(红) is 214'的儿子   left child  父亲是    214
344(红) is 214'的儿子  right child  父亲是    214

== 删除节点: 40
== 树的详细信息: 
60(B) is root
30(黑) is 60'的儿子   left child  父亲是     60
12(黑) is 30'的儿子   left child  父亲是     30
20(红) is 12'的儿子  right child  父亲是     12
45(红) is 30'的儿子  right child  父亲是     30
34(黑) is 45'的儿子   left child  父亲是     45
50(黑) is 45'的儿子  right child  父亲是     45
56(红) is 50'的儿子  right child  父亲是     50
80(黑) is 60'的儿子  right child  父亲是     60
70(黑) is 80'的儿子   left child  父亲是     80
67(红) is 70'的儿子   left child  父亲是     70
123(红) is 80'的儿子  right child  父亲是     80
90(黑) is 123'的儿子   left child  父亲是    123
214(黑) is 123'的儿子  right child  父亲是    123
213(红) is 214'的儿子   left child  父亲是    214
344(红) is 214'的儿子  right child  父亲是    214

== 删除节点: 30
== 树的详细信息: 
60(B) is root
34(黑) is 60'的儿子   left child  父亲是     60
12(黑) is 34'的儿子   left child  父亲是     34
20(红) is 12'的儿子  right child  父亲是     12
50(红) is 34'的儿子  right child  父亲是     34
45(黑) is 50'的儿子   left child  父亲是     50
56(黑) is 50'的儿子  right child  父亲是     50
80(黑) is 60'的儿子  right child  父亲是     60
70(黑) is 80'的儿子   left child  父亲是     80
67(红) is 70'的儿子   left child  父亲是     70
123(红) is 80'的儿子  right child  父亲是     80
90(黑) is 123'的儿子   left child  父亲是    123
214(黑) is 123'的儿子  right child  父亲是    123
213(红) is 214'的儿子   left child  父亲是    214
344(红) is 214'的儿子  right child  父亲是    214

== 删除节点: 60
== 树的详细信息: 
67(B) is root
34(黑) is 67'的儿子   left child  父亲是     67
12(黑) is 34'的儿子   left child  父亲是     34
20(红) is 12'的儿子  right child  父亲是     12
50(红) is 34'的儿子  right child  父亲是     34
45(黑) is 50'的儿子   left child  父亲是     50
56(黑) is 50'的儿子  right child  父亲是     50
80(黑) is 67'的儿子  right child  父亲是     67
70(黑) is 80'的儿子   left child  父亲是     80
123(红) is 80'的儿子  right child  父亲是     80
90(黑) is 123'的儿子   left child  父亲是    123
214(黑) is 123'的儿子  right child  父亲是    123
213(红) is 214'的儿子   left child  父亲是    214
344(红) is 214'的儿子  right child  父亲是    214

== 删除节点: 90
== 树的详细信息: 
67(B) is root
34(黑) is 67'的儿子   left child  父亲是     67
12(黑) is 34'的儿子   left child  父亲是     34
20(红) is 12'的儿子  right child  父亲是     12
50(红) is 34'的儿子  right child  父亲是     34
45(黑) is 50'的儿子   left child  父亲是     50
56(黑) is 50'的儿子  right child  父亲是     50
80(黑) is 67'的儿子  right child  父亲是     67
70(黑) is 80'的儿子   left child  父亲是     80
214(红) is 80'的儿子  right child  父亲是     80
123(黑) is 214'的儿子   left child  父亲是    214
213(红) is 123'的儿子  right child  父亲是    123
344(黑) is 214'的儿子  right child  父亲是    214

== 删除节点: 70
== 树的详细信息: 
67(B) is root
34(黑) is 67'的儿子   left child  父亲是     67
12(黑) is 34'的儿子   left child  父亲是     34
20(红) is 12'的儿子  right child  父亲是     12
50(红) is 34'的儿子  right child  父亲是     34
45(黑) is 50'的儿子   left child  父亲是     50
56(黑) is 50'的儿子  right child  父亲是     50
214(黑) is 67'的儿子  right child  父亲是     67
123(红) is 214'的儿子   left child  父亲是    214
80(黑) is 123'的儿子   left child  父亲是    123
213(黑) is 123'的儿子  right child  父亲是    123
344(黑) is 214'的儿子  right child  父亲是    214

== 删除节点: 20
== 树的详细信息: 
67(B) is root
34(黑) is 67'的儿子   left child  父亲是     67
12(黑) is 34'的儿子   left child  父亲是     34
50(红) is 34'的儿子  right child  父亲是     34
45(黑) is 50'的儿子   left child  父亲是     50
56(黑) is 50'的儿子  right child  父亲是     50
214(黑) is 67'的儿子  right child  父亲是     67
123(红) is 214'的儿子   left child  父亲是    214
80(黑) is 123'的儿子   left child  父亲是    123
213(黑) is 123'的儿子  right child  父亲是    123
344(黑) is 214'的儿子  right child  父亲是    214

== 删除节点: 50
== 树的详细信息: 
67(B) is root
34(黑) is 67'的儿子   left child  父亲是     67
12(黑) is 34'的儿子   left child  父亲是     34
56(黑) is 34'的儿子  right child  父亲是     34
45(红) is 56'的儿子   left child  父亲是     56
214(黑) is 67'的儿子  right child  父亲是     67
123(红) is 214'的儿子   left child  父亲是    214
80(黑) is 123'的儿子   left child  父亲是    123
213(黑) is 123'的儿子  right child  父亲是    123
344(黑) is 214'的儿子  right child  父亲是    214

== 删除节点: 80
== 树的详细信息: 
67(B) is root
34(黑) is 67'的儿子   left child  父亲是     67
12(黑) is 34'的儿子   left child  父亲是     34
56(黑) is 34'的儿子  right child  父亲是     34
45(红) is 56'的儿子   left child  父亲是     56
214(黑) is 67'的儿子  right child  父亲是     67
123(黑) is 214'的儿子   left child  父亲是    214
213(红) is 123'的儿子  right child  父亲是    123
344(黑) is 214'的儿子  right child  父亲是    214

== 删除节点: 123
== 树的详细信息: 
67(B) is root
34(黑) is 67'的儿子   left child  父亲是     67
12(黑) is 34'的儿子   left child  父亲是     34
56(黑) is 34'的儿子  right child  父亲是     34
45(红) is 56'的儿子   left child  父亲是     56
214(黑) is 67'的儿子  right child  父亲是     67
213(黑) is 214'的儿子   left child  父亲是    214
344(黑) is 214'的儿子  right child  父亲是    214

== 删除节点: 12
== 树的详细信息: 
67(B) is root
45(黑) is 67'的儿子   left child  父亲是     67
34(黑) is 45'的儿子   left child  父亲是     45
56(黑) is 45'的儿子  right child  父亲是     45
214(黑) is 67'的儿子  right child  父亲是     67
213(黑) is 214'的儿子   left child  父亲是    214
344(黑) is 214'的儿子  right child  父亲是    214

== 删除节点: 34
== 树的详细信息: 
67(B) is root
45(黑) is 67'的儿子   left child  父亲是     67
56(红) is 45'的儿子  right child  父亲是     45
214(红) is 67'的儿子  right child  父亲是     67
213(黑) is 214'的儿子   left child  父亲是    214
344(黑) is 214'的儿子  right child  父亲是    214

== 删除节点: 45
== 树的详细信息: 
67(B) is root
56(黑) is 67'的儿子   left child  父亲是     67
214(红) is 67'的儿子  right child  父亲是     67
213(黑) is 214'的儿子   left child  父亲是    214
344(黑) is 214'的儿子  right child  父亲是    214

== 删除节点: 56
== 树的详细信息: 
214(B) is root
67(黑) is 214'的儿子   left child  父亲是    214
213(红) is 67'的儿子  right child  父亲是     67
344(黑) is 214'的儿子  right child  父亲是    214

== 删除节点: 67
== 树的详细信息: 
214(B) is root
213(黑) is 214'的儿子   left child  父亲是    214
344(黑) is 214'的儿子  right child  父亲是    214

== 删除节点: 213
== 树的详细信息: 
214(B) is root
344(红) is 214'的儿子  right child  父亲是    214

== 删除节点: 214
== 树的详细信息: 
344(B) is root

== 删除节点: 344
== 树的详细信息: 

Disconnected from the target VM, address: '127.0.0.1:52204', transport: 'socket'

Process finished with exit code 0
