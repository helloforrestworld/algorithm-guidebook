## Binary Search

假设你要在 1-100 的数字中找到一个目标数如：65，更有效率的方式是从 50 开始找，50 小于 65，然后取 50-65 的中间值继续重复第一步。每次排除一半的数字。一般而言，对于包含 n 个元素的列表，用二分查找最多需要 log2n 步，而简单查找最多需要 n 步，用大 O 表示法时间复杂度为 logN

函数 binary_search 接受一个有序数组和一个元素。如果指定的元素包含在数组中，这个函数将返回其位置。你将跟踪要在其中查找的数组部分——开始时为整个数组。

```js
let low = 0;
let high = list.length - 1;

// 每次都去检查中间元素
let mid = (low + high) / 2;
let guess = list[mid];

// 如果数字猜小了，就相应去修改low
if (guess < item) {
  low = mid + 1;
}

// 如果数组猜大了，就相应去修改high
if (guess > item) {
  high = mid - 1;
}
```

完整代码如下：

```js
function binary_search(list, item) {
  let low = 0;
  let high = list.length - 1;
  let mid;
  let guess;

  while (low <= high) {
    mid = Math.floor((low + high) / 2);
    guess = list[mid];
    if (guess === item) {
      return mid;
    } else if (guess > item) {
      high = mid - 1;
    } else {
      low = mid + 1;
    }
  }
  return null;
}
```
