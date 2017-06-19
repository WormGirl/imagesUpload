# 移动端H5图片压缩上传
部分API的兼容性请参照[caniuse](www.caniuse.com)：
## 使用到的库
* [移动端H5图片压缩](https://github.com/CommanderXL/imgResize)
* [AlloyFinger](https://github.com/AlloyTeam/AlloyFinger)
# 使用方法

```javascript
<div class="upload-wrap">
            <img id="previewResult" />
            <button class="button blue rarrow file-input-mask"><input type="file" id="file" accept="image/*" /></button>
        </div>
        <img id="preview" />
```

```javascript
   (function () {
    var _input = document.querySelector('#file')
    _input.addEventListener('change', function (e) {
      canvasResize(this.files[0], {
        crop: false,
        quality: 0.9,
        rotate: 0,
        callback(baseStr) {
            $("#preview").attr("src",baseStr).hide();
            var crop_btn = document.querySelector("#crop_btn");
            new AlloyCrop({
                image_src: $("#preview").attr("src"),
                width: 300,
                height: 300,
                ok_text: "确定", // optional parameters , the default value is ok
                cancel_text: "取消", // optional parameters , the default value is cancel
                ok: function (base64, canvas) {
                    $("#previewResult").attr('src',base64);
                    $(".file-input-mask").css("opacity","0");
                },
                cancel: function () {
                }
            });
        }
      })
    })
   })();
```
# demo地址
* [demo点我](http://WormGirl.github.io/imagesUpload/demo.html)
