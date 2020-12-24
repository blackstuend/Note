# off-canvas 點擊旁邊自動消失

1. 先去判斷是否點擊在整個頁面上
2. 再去偵測點擊在哪裡 然後停止程序即可!!



```
        $(window).click(function() {
            $(".header-side").removeClass("header-side-show");
        });
        
        $('.header-nav-sidebar').click(function(event){
            event.stopPropagation();
        });
        $('.header-side').click(function(event){
            event.stopPropagation();
        });
```