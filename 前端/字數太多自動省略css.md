# 字數太多自動變成...的Css


* 使用chrome

* 須注意text不要去調整高度，需用fit-content，否則會因為高度變了overflow會因為高度變了則有些文字露出來而失效，所以要注意padding與height的使用

* chrome的使用方式-webkit，由於其他瀏覽器沒有這個外掛，所以chrome可直接寫

```css
.text {
    border:1px solid black;
    margin: auto;
    width: 300px;
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
}
```


* 其他瀏覽器，較為廣泛
    * 使用偽元素以及line-height來算出需要幾行的文字算法是height/line-height = 行數，超出的一樣使用overflow:hidden
```css
.text {
    position: relative;
    margin: auto;
    width: 300px;
    font-size: 16px;
    line-height: 16px;
    height: 32px;
    overflow: hidden;
}
.text::after {
    content: '...';
    position: absolute;
    right: 0;
    bottom: 0;
}
```