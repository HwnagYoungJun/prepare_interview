# 정렬

## 1. Bubble Sort(거품 정렬)

> 서로 인접한 두 원소의 대소를 배교하고, 조건에 맞지 않다면 자리를 교환하며 정렬하는 알고리즘



### 과정

1. 첫 번째 탐색에 첫 번째 원소와 두 번째 원소, 두 번째 원소와 세 번째 원소 이런 식으로 조건에 맞지 않으면 교환 합니다.
2. 첫 번째 탐색 떄 가장 큰 원소가 맨 뒤로 이동하므로 두 번째 탐색에서는 맨 뒤의 원소는 정렬에서 제외됩니다.



### 코드 (Python)

```python
def bubble_sort(target):
    len_target = len(target)
    
    for i in range(len_target):
        for j in range(1, len_target - i):
            if target[j - 1] > target[j]:
                # swap
                target[j - 1], target[j] = target[j], target[j - 1]
```



### 시간복잡도

> (n - 1)n / 2 이므로 O(n^2)의 복잡도를 가지고 평균, 최악, 최선의 경우 모두 O(n^2)으로 동일합니다.



## 2. Selection Sort(선택 정렬)

> 해당 위치에 맞는 자료를 선택하여 위치를 교환하는 정렬 알고리즘



### 과정

1. 주어진 배열에서 최소값을 찾습니다.
2. 그 값을 맨 앞에 위치한 값과 교체합니다.
3. 맨 처음 위치를 뺀 나머지 배열을 같은 방법으로 교체합니다.



### 코드(Python)

```python
def selection_sort(target):
    len_target = len(target)
    
    for i in range(len_target):
        min_value = float('inf')
        min_index = i
        for j in range(i, len_target):
            if min_value > target[j]:
                min_value = target[j]
                min_index = j
        # swap
        target[i], target[min_index] = target[min_index], target[i]
```



### 시간복잡도

> 거품정렬과 동일하게 최악, 최선, 평균 모두 O(n^2)의 시간복잡도를 가집니다.



## 3. Insertion Sort(삽입 정렬)

>  2번째 원소 부터 시작하여 그 앞의 원소들과 비교하여 삽입할 위치를 지정한 후, 원소를 뒤로 옮기고 지정된 자리에 자료를 삽입하는 정렬 알고리즘



### 과정

1. 정렬은 2번째 위치의 값을 temp의 저장합니다.
2. temp와 이전에 있는 원소들을 비교하면서 삽입해 나갑니다.
3. 1번으로 돌아가 다음 위치의 값을 temp에 저장하고, 반복합니다.



### 코드(Python)

```python
def insertion_sort(target):
    len_target = len(target)
    
    for i in range(1, len_target):
        temp = target[i]
        prev = i - 1
       	while prev >= 0 and target[prev] > temp:
            target[prev + 1] = target[prev]
            prev -= 1
        
        target[prev + 1] = temp
```



### 시간복잡도

> 모두 정렬이 되어있는 경우라면 한번씩 밖에 비교를 안하므로 O(n)의 시간복잡도를 가지게 됩니다. 또한 오버헤드가 매우 적습니다. 평균과 최악의 경우에는 O(n^2)의 시간복잡도를 가지게 됩니다.



### 4.  Quick Sort(퀵 정렬)



### 코드

```python
def quick_sort(arr):

    def sort(left, right):
        if left >= right:
            return
        
        mid = partition(left, right)
        sort(left, mid - 1)
        sort(mid, right)

    def partition(left, right):
        pivot = arr[(left + right) // 2]
        while left <= right:
            while arr[left] < pivot:
                left += 1
            while arr[right] > pivot:
                right -= 1
            if left <= right:
                arr[left], arr[right] = arr[right], arr[left]
                left += 1
                right -= 1
            
        return left
    
    return sort(0, len(arr) - 1)
```