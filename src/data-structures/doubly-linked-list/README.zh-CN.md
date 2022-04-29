# 双向链表

在计算机科学中, 一个 **双向链表(doubly linked list)** 是由一组称为节点的顺序链接记录组成的链接数据结构。每个节点包含两个字段，称为链接，它们是对节点序列中上一个节点和下一个节点的引用。开始节点和结束节点的上一个链接和下一个链接分别指向某种终止节点，通常是前哨节点或null，以方便遍历列表。如果只有一个前哨节点，则列表通过前哨节点循环链接。它可以被概念化为两个由相同数据项组成的单链表，但顺序相反。

![Doubly Linked List](https://upload.wikimedia.org/wikipedia/commons/5/5e/Doubly-linked-list.svg)

两个节点链接允许在任一方向上遍历列表。

在双向链表中进行添加或者删除节点时,需做的链接更改要比单向链表复杂得多。这种操作在单向链表中更简单高效,因为不需要关注一个节点（除第一个和最后一个节点以外的节点）的两个链接,而只需要关注一个链接即可。

## 基础操作的伪代码

### 插入

```text
Add(value)
  Prev: value 是要插入的值
  Post: value 被插入到列表的尾部
  n ← node(value)
  if head = ø
    head ← n
    tail ← n
  else
    n.previous ← tail
    tail.next ← n
    tail ← n
  end if
end Add
```

### 删除

```text
Remove(head, value)
  Prev: head 是列表里的第一个节点
       value 是要从列表中删除的值
  Post: value 若从列表中被删除, 返回 true; 否则返回 false
  if head = ø
    return false
  end if
  if value = head.value
    if head = tail
      head ← ø
      tail ← ø
    else
      head ← head.next
      head.previous ← ø
    end if
    return true
  end if
  n ← head.next
  while n != ø and value !== n.value
    n ← n.next
  end while
  if n = tail
    tail ← tail.previous
    tail.next ← ø
    return true
  else if n != ø
    n.previous.next ← n.next
    n.next.previous ← n.previous
    return true
  end if
  return false
end Remove
```

### 反向遍历

```text
ReverseTraversal(tail)
  Prev: tail 是要遍历的列表的最后一个节点
  Post: 列表被反向遍历
  n ← tail
  while n != ø
    yield n.value
    n ← n.previous
  end while
end Reverse Traversal
```

## 复杂度

## 时间复杂度

| Access    | Search    | Insertion | Deletion  |
| :-------: | :-------: | :-------: | :-------: |
| O(n)      | O(n)      | O(1)      | O(1)      |

### 空间复杂度

O(n)

## 参考

- [Wikipedia](https://en.wikipedia.org/wiki/Doubly_linked_list)
- [YouTube](https://www.youtube.com/watch?v=JdQeNxWCguQ&t=7s&index=72&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
