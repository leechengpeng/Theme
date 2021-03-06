---
title: STL vector
date: 2017.06.20
tags:
  - STL
  - vector 
categories: Data Structure
---

### 1. iterator
vector<T>的迭代器实际上是其类型T的指针，定义如下：
```
typedef T* iterator;
```
因为vector维护的是线性空间，普通指针即可满足迭代器的所有操作：*、->、++、--、-、+、-=、+=

### 2. vector的容量(capacity)大于其实际存储量(size)
为了提高vector的空间配置效率，其实际分配的大小通常比用户需求量更大一些。**SGI STL**的分配规则为：
* 如果vector中的容量为0，则将其容量扩容为1
* 如果vector中的容量大于0，则配置其容量为原大小的2倍。

按照2倍的分配原则，其前半段用来放置原有数据，后半段用来放置新数据。

不同的STL实现库可能分配原则稍有不同，但都会通过某种策略进行扩容。需要特别注意的是：**一旦vector重新分配空间，原有数据会被转移到新分配的空间，指向原vector的迭代器都会失效**。

