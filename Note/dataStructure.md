## 简单数据结构
* 有序数据结构

    栈、队列、链表

    有序数据结构省空间(存储空间小)
* 无序数据结构

    集合、字典、散列表

    无序数据结构省时间(读取时间快)
## 复杂数据结构
* 树、堆
* 图

### 排序
* 快速排序

1.随机选择数组中的一个数A，以这个数为基准

2.其他数字跟这个数进行比较，比这个数小的放在其左边，大的放到其右边

3.经过一次循环之后，A左边为小于A的，右边为大于A的

4.这时候将左边和右边的数再递归上面的过程

````
const testArr = [67, 33, 12, 34, 11, 87, 54];
function quickSort(arr) {
    if (arr.length <= 1) {
        return arr;
    }
    let pivotIndex = Math.floor(arr.length / 2);
    let pivot = arr.splice(pivotIndex, 1)[0];
    let left = [];
    let right = [];
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] < pivot) {
            left.push(arr[i]);
        } else {
            right.push(arr[i]);
        }
    }
    return quickSort(left).concat([pivot], quickSort(right));
}
````

