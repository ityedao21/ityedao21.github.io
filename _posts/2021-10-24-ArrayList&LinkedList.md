---
layout: article
title: "Java基础学习-ArrayList&LinkedList"
---

# ArrayList集合底层原理

- ArrayList底层是基于数组实现的：根据索引定位元素快，增删需要做元素的移位操作。
- 第一次创建集合并添加第一个元素的时候，在底层创建一个默认长度为10的数组。

```java
List<String> list = new ArrayList<>();
list.add("a");
```



> 思考：为何ArrayList查询快、增删元素相对较慢?
>
> tips：size

# LinkedList的特点

- 底层数据结构是双链表，查询慢，首尾操作的速度是极快的，所以多了很多首尾操作的特有API。

| 方法名称                  | 说明                             |
| ------------------------- | -------------------------------- |
| public void addFirst(E e) | 在该列表开头插入指定的元素       |
| public void addLast(E e)  | 将指定的元素追加到此列表的末尾   |
| public E getFirst()       | 返回此列表中的第一个元素         |
| public E getLast()        | 返回此列表中的最后一个元素       |
| public E removeFirst()    | 从此列表中删除并返回第一个元素   |
| public E removeLast()     | 从此列表中删除并返回最后一个元素 |

# 问题引出

#### 当我们从集合中找出某个元素并删除的时候可能出现一种并发修改异常问题



## 哪些遍历存在问题？

> 迭代器遍历集合且直接用集合删除元素的时候可能出现。
>
> 增强for循环遍历集合且直接用集合删除元素的时候可能出现。

## 哪种遍历且删除元素不出问题

>迭代器遍历集合但是用迭代器自己的删除方法操作可以解决。
>
>使用for循环遍历并删除元素不会存在这个问题。

