# 20221215 工作筆記

## `script` tag 的 async & defer

瀏覽器解析 HTML 是一行一行由上往下的順序向下讀取。在傳統的寫法中，當瀏覽器讀到 `<script>` 時就會**暫停解析 DOM** 然後立刻開始下載 `<script>` 的資源，並在資源下載完成後立刻執行。

這樣的特性可能會導致以下的問題：

1. DOM tree 在尚未建構完全時就執行了 JavaScript ，如此一來某些需要操作 DOM 的程式碼可能無法順利運作。
2. 等待資源下載和執行的過程中，使用者可能會卡在白畫面一段時間，造成不好的使用者體驗。

在以往的解決方法中，開發者只需要將所有的 `<script>` 標籤都移動到 `<body>` 標籤內的最後，就可以避免在 DOM tree 尚未建構完成時就執行 JavaScript 的問題。不過隨著網站開發的功能與項目越來越龐大和複雜，若要等到整個 DOM tree 都載入完成後才開始下載 `<script>` 資源的話，在網站讀取完成到使用者可操作的這段時間還是會有明顯的延遲感。

於是在 HTML4 和 HTML5 就分別新增了 `defer` 和 `async` 屬性，用來幫助開發者控制 `<script>` 內資源的載入及執行順序，以避免 DOM 的解析被資源下載時卡住。

- defer
  > When set, this boolean attribute provides a hint to the user agent that the script is not going to generate any document content( e.g. no "document.write" in javascript )and thus, **the user agent can continue parsing and rendering.**

因此加上 `defer` 屬性後，瀏覽器就會略過需要資料下載的 `<script>` 標籤繼續解析和渲染畫面。

- async
  > If the async attribute is present, then the script will be executed asynchronously, as soon as it's available.

在 `<script>` 加上 `async` 屬性後，與 `defer` 相同的是會在背景執行下載，但不同的是當下載完成會**馬上暫停 DOM 解析**並開始執行 JavaScript 。不過也因為下載完成後就會立即執行，所以很難保證執行的先後順序。

放上一張 Stack Overflow 的解答中附上的一個圖解，清楚很多。

![defer&async](/img/defer%26async.png)

---

### 參考文章

- [前端三十 - 成為更好的前端工程師](https://ithelp.ithome.com.tw/users/20111380/ironman/2635)
- [Script Tag - async & defer](https://stackoverflow.com/questions/10808109/script-tag-async-defer)

---

### 明天可研究項目

- [認識 JavaScript Reduce](https://medium.com/unalai/%E8%AA%8D%E8%AD%98-javascript-reduce-940806267bfb)
- [JavaScript reduce 在做什麼？](https://w3c.hexschool.com/blog/a2cb755f)
