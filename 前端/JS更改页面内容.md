> [!ERROR] 使用 js 更改页面中所有元素为 sidebar-section-header 的内容

```js
// 确保DOM内容完全加载后再执行
document.addEventListener('DOMContentLoaded', function() {
    // 获取所有 class 为 tree-header 的元素
    var treeHeaders = document.getElementsByClassName('graph-view-wrapper');
    // 遍历每个 tree-header 元素
    for (var i = 0; i < treeHeaders.length; i++) {
        // 在每个 tree-header 元素下获取 class 为 sidebar-section-header 的子元素
        var sidebarHeaders = treeHeaders[i].getElementsByClassName('sidebar-section-header');
        // 遍历并更改这些子元素的文本内容
        for (var j = 0; j < sidebarHeaders.length; j++) {
            sidebarHeaders[j].textContent = '关系图谱';
        }
    }
});
```