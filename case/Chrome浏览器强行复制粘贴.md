# 有些网页上的文字无法复制，有些输入框无法粘贴

## Chrome 无法复制

- 快捷键 "Command + p"
- 可以愉快地选取打印预览页面的文字了

## Chrome 无法粘贴

- 快捷键 F12 或 鼠标右键 选择 inspect(审查元素)
- 点击 Console
- 输入以下内容
    - > javascript:(function() { function R(a){ona = "on"+a; if(window.addEventListener) window.addEventListener(a, function (e) { for(var n=e.originalTarget; n; n=n.parentNode) n[ona]=null; }, true); window[ona]=null; document[ona]=null; if(document.body) document.body[ona]=null; } R("contextmenu"); R("click"); R("mousedown"); R("mouseup"); R("selectstart");})()
- 若仍然没法复制粘贴，按F1，勾选以下：
    - color-code resource types
    - disabale javascript
