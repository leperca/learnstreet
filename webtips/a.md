# 拖放文件并且读取

- HTML容器
- 阻止默认拖放行为
- 自定义新的拖放行为
- 文件读取

```html
<div id="container" style="border:1px solid green ; width:400px;height:400px">
    <p>Drop File</p>
    <p id="pp">sf</p>
</div>

<script>
    // container
    container = document.getElementById("container")
    pp = document.getElementById("pp")

    // preventDefault
    document.ondrop = function (e) {
        e.preventDefault();
    };
    document.ondragover = function (e) {
        e.preventDefault();
    };

    // define new drop
    container.ondrop = function (e) {
        let file = e.dataTransfer.files[0]
        readFile(file)
    };

    // handle the file
    function readFile(file) {
        let fr = new FileReader();
        fr.onload = function (e) {
            pp.innerHTML = e.target.result
        }
        fr.readAsText(file)
    }
</script>
```
结果看a.html
