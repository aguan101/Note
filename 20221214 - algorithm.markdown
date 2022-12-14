# 20221214 工作筆記

## Algorithm 演算法

> 演算法就是解決問題的方法。

---

## Big O

> Big O 是用來描述一個演算法再輸入 n 個東西時，總執行時間與 n 的關係。

常見的時間複雜度有以下幾種：

- Big O(1)

  不管你搜尋的基數(n)大小，都會在同樣時間跑完。

- Big O(n)

  執行時間會跟著 n 等比例變多。

- Big O(log n)

  搜尋的基數為 n 時，執行步驟是 log n 。

- Big O(n²)

  效能比較差的演算法，像是包了兩層 for loop 的都是屬於此種演算法。

- Big O(2^n)

  常見的時間複雜度中效能很差的一個，最有名的 Fibonacci 就是使用這種演算法。

### 重點整理

1. Big O 是評量演算法的時間複雜度。
2. 遇到問題時通常會希望演算法比 Big O(n²) 快，如果能到達 Big O(n)、Big O(log n)、Big O(1) 就會更理想。
3. 演算法的速度不是以秒計算，而是以步驟次數來做計算。
4. Big O 會以最壞情況紀錄 n 的次數。
5. 時間複雜度會省略所有係數，例如 Big O(2n² + n)，會簡化成 O(n²)

---

## Array 陣列

> 一個儲存資料的箱子，而且是連續性的存放，所以當要拿特定位置的值會非常快速。時間複雜度是 Big O(1) ，但如果你忘了是哪個位置的話，時間複雜就會變成 Big O(n) 。

所以遇到需要處理順序的問題時，通常 Array 就是最佳解。不過相對的壞處就是當你想要加入或移除某一個值時，整個 Array 都會影響到。

以下是幾點在選擇陣列方法時要特別注意的地方：

1. 經過 Array 方法後到底回傳了什麼？
2. 會不會改變原本的 Array ？

### Basic Array Method

1. Array.prototype.push(element)
2. Array.prototype.unshift(element)
3. Array.prototype.pop()
4. Array.prototype.shift()
5. Array.prototype.concat()

### Filter / Find something Array Method

1. Array.prototype.findIndex(item, index, array)
2. Array.prototype.find(item, index, array)
3. Array.prototype.filter(item, index, array)
4. Array.prototype.forEach(item, index, array)
5. Array.prototype.map(item, index, array)
6. Array.prototype.some(item, index, array)
7. Array.prototype.every(item, index, array)

### Special Array Method

1. Array.prototype.reduce(accumulator, currentValue, currentIndex, array[, initialValue])

- accumulator : 前一個回傳的值，會從 initialValue 開始做計算。如果沒有設定 initialValue 的話，就會從陣列索引值 index 為 0 的值開始計算。
- currentValue : 現在的值
- currentIndex : 現在的參數位置（索引值）
- array : 全部的陣列
- initialValue : 設定的初始值（可以不設定）

### Order Array Method

1. Array.prototype.sort(compareFunction)
2. Array.prototype.reverse()

### Operation Array Method

1. Array.prototype.slice(start, end)
2. Array.prototype.splice(start, deleteCount, item1, item2)
3. Array.prototype.indexOf(searchElement)
4. Array.prototype.join(separator)
5. Array.prototype.includes(searchElement, fromIndex)

### 參考文章

- [What's an algorithm?](https://www.youtube.com/watch?v=6hfOvs8pY1k)
- [前端工程師用 JavaScript 學演算法 系列](https://ithelp.ithome.com.tw/users/20106426/ironman/2136)
- [LeetCode Note](https://hannahpun.gitbook.io/leetcode-note/tools/array-method)

---

<!-- ### 明天可研究項目 -->
