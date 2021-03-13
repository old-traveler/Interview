
## HashMap 为什么要用头插法
插入的速度更快
1.8之后改为尾插法，避免链表成环

## HashMap为啥要用红黑树不用AVL树
红黑树和AVL树都是最常用的平衡二叉搜索树，它们的查找、删除、修改都是O(lgn) time

AVL树和红黑树有几点比较和区别：
* （1）AVL树是更加严格的平衡，因此可以提供更快的查找速度，一般读取查找密集型任务，适用AVL树。
* （2）红黑树更适合于插入修改密集型任务。
* （3）通常，AVL树的旋转比红黑树的旋转更加难以平衡和调试。

总结：
* （1）AVL以及红黑树是高度平衡的树数据结构。它们非常相似，真正的区别在于在任何添加/删除操作时完成的旋转操作次数。
* （2）两种实现都缩放为a O(lg N)，其中N是叶子的数量，但实际上AVL树在查找密集型任务上更快：利用更好的平衡，树遍历平均更短。另一方面，插入和删除方面，AVL树速度较慢：需要更高的旋转次数才能在修改时正确地重新平衡数据结构。
* （3）在AVL树中，从根到任何叶子的最短路径和最长路径之间的差异最多为1。在红黑树中，差异可以是2倍。
* （4）两个都给O（log n）查找，但平衡AVL树可能需要O（log n）旋转，而红黑树将需要最多两次旋转使其达到平衡（尽管可能需要检查O（log n）节点以确定旋转的位置）。旋转本身是O（1）操作，因为你只是移动指针。