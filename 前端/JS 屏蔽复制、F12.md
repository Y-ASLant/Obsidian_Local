## JS 屏蔽复制

```html
在.html中无 $ 符号，仅在.js中有
    <script type = "text/javascript" >
        $(document).ready(function () {
            // 禁止右键
            $(document).bind("contextmenu", function () { return false; });
            // 禁止选择
            $(document).bind("selectstart", function () { return false; });
            // 禁止Ctrl+C 和Ctrl+A
            $(document).keydown(function (event) {
                if ((event.ctrlKey && event.which == 67) || (event.ctrlKey && event.which == 86)) {
                    //alert("Sorry,版权个人所有,禁止复制");
                    return false;
                }
            });
        });
// 屏蔽F12键
document.addEventListener('keydown', function (e) {
    if (e.key === 'F12') {
        e.preventDefault();
    }
});
</script>
```

  ```js
  <script type="text/javascript">
      // 禁用右键菜单
      document.addEventListener('contextmenu', function (e) {
          e.preventDefault();
      });
  
      // 禁用文本选择复制
      document.addEventListener('selectstart', function (e) {
          e.preventDefault();
      });
      // 屏蔽F12键
      document.addEventListener('keydown', function (e) {
          if (e.key === 'F12') {
              e.preventDefault();
          }
      });
  </script>
  ```

```Js
/*禁用F12*/
document.onkeydown = function() {
if (window.event && window.event.keyCode == 123) {
  layer.msg("大佬，别扒了！不妨加个友链？");
        event.keyCode = 0;
        event.returnValue = false;
        }
    }
```


