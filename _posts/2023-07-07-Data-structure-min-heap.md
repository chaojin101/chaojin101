---
title: Data structure min binary heap
categories: ["data structure"]
---

# Definition

ADT:

the amount of vals in heap is `n`.

pop() -> val `O(log(n))` get and delete the min val.

push(val) -> None `O(log(n))` insert a val into heap.

top() -> val `O(1)` get the min val.

# Implementation

Here is a simple python implementation of min heap.

```py
class MinHeap:
    def __init__(self, vals: list[int]):
        self.__heap = [val for val in vals]
        for i in range(len(self.__heap) // 2 - 1, -1, -1):
            self.__heapify_down(i)

    def push(self, val: int):
        self.__heap.append(val)
        self.__heapify_up(self.size() - 1)

    def pop(self):
        if self.size() <= 0:
            raise Exception("can't pop an empty heap")
        item = self.__heap[0]
        self.__heap[0] = self.__heap[self.size() - 1]  # replace root with last item
        self.__heap.pop()  # remove last slot
        self.__heapify_down(0)
        return item

    def top(self):
        if self.size() <= 0:
            raise Exception("can't get top of an empty heap")
        return self.__heap[0]

    def size(self):
        return len(self.__heap)

    def __heapify_up(self, index: int):
        cur_index = index
        while True:
            parent_index = self.__get_parent_index(cur_index)
            if parent_index < 0 or parent_index >= self.size():
                break
            if self.__less(parent_index, cur_index):
                break
            self.__swap(parent_index, cur_index)
            cur_index = parent_index

    def __heapify_down(self, index: int):
        cur_index = index
        while True:
            left_child_index = self.__get_left_child_index(cur_index)
            if left_child_index >= self.size() or left_child_index < 0:
                break
            min_child_index = left_child_index
            right_child_index = self.__get_right_child_index(cur_index)
            if 0 <= right_child_index < self.size() and self.__less(
                right_child_index, left_child_index
            ):
                min_child_index = right_child_index
            if self.__less(cur_index, min_child_index):
                break
            self.__swap(min_child_index, cur_index)
            cur_index = min_child_index

    def __less(self, i: int, j: int):
        return self.__heap[i] < self.__heap[j]

    def __get_parent_index(self, index: int):
        return (index - 1) // 2

    def __get_left_child_index(self, index: int):
        return 2 * index + 1

    def __get_right_child_index(self, index: int):
        return 2 * index + 2

    def __swap(self, i: int, j: int):
        self.__heap[i], self.__heap[j] = self.__heap[j], self.__heap[i]


if __name__ == "__main__":
    heap = MinHeap([2, 1, 3, 4, 5])
    heap.push(0)
    print(heap.pop())
    print(heap.pop())
    print(heap.pop())
    print(heap.pop())
    print(heap.pop())
    print(heap.pop())

```

Output:

```sh
0
1
2
3
4
5
```

# Note

- the index of left child is `2 * index + 1`.
- the index of right child is `2 * index + 2`.
- the index of parent is `(index - 1) // 2`.
- the index of last non-leaf node is `(len(heap) // 2 - 1)`.

---

in `__init__` method, we start from the last non-leaf node to the root node, do heapify down for each node to construct the min heap.

```py
for i in range(len(self.__heap) // 2 - 1, -1, -1):
    self.__heapify_down(i)
```

# Reference

[animation for understanding](https://www.youtube.com/watch?v=AE5I0xACpZs)

[whiteboard drawing for understanding](https://www.youtube.com/watch?v=g9YK6sftDi0)

[simple python implementation](https://www.youtube.com/watch?v=hkyzcLkmoBY)
