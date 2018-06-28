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
