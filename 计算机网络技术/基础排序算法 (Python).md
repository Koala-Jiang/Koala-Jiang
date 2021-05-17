# 基础排序算法 (Python)

**按照从小到大的顺序排列**



```python
def swap(lst, index1, index2):
    temp = lst[index1]
    lst[index1] = lst[index2]
    lst[index2] = temp
```



## Selection Sort

在后续所有项中找到最小项，与第i项做交换

```python
def sltSort(lst):
    for i in range(len(lst) - 1):
        min_index = i
        for j in range(i+1, len(lst)):  # look for the max in inner loop
            if lst[j] < lst[min_index]:
                min_index = j
        if min_index != i:  # get max for each outer iteration
            swap(lst, i, min_index)
```

## Bubble Sort

每次与后一位比较，如果更大，则后移

```python
def bbSort(lst):  # put bigger to right, one by one
    for i in range(len(lst) - 1):
        for j in range(len(lst)-1-i): # no need to iter right which are in order
            if lst[j] > lst[j + 1]:
                swap(lst, j, j+1)
```

## Insertion Sort

类似于打牌，抽取i+1位，然后和前位比较，如果待插入值比较小，前位后移，最后将待插入放在preIndex+1处（空）



```python
def instSort(lst):
    for i in range(len(lst)-1):
        itemToInsert, preIndex = lst[i+1], i
        while preIndex >= 0 and itemToInsert < lst[preIndex]:
            lst[preIndex+1] = lst[preIndex]
            preIndex -= 1
        lst[preIndex + 1] = itemToInsert  # put itemToInsert into place
```



