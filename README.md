# why 
scale.js原代码无法运行（代码有两处小错误）

# scale.js
High-quality scale function for canvas and image element.
If scale factor < 1, then algorithm for downscale is used, other than that, bicubic algorithm is used.

# Performance
一张6M的图(6000*4000px)，压缩到750px：
elapsed: ~5s
size: 600K(png), 400K(jpg)
clarity: 非常清晰

# 此算法存在的问题
太慢，生成的图片太大


## How to use

    <html><body>
      <canvas id="inputCanvas"></canvas>
      <img id="inputImage" src="..." />
      <canvas id="exportCanvas"></canvas>
      
      <script src="src/scale.js" />
      <script>
      (function(){
        var inputCanvas = document.getElementById("inputCanvas");
        var inputImage = document.getElementById("inputImage");

        // 返回<canvas> dom element
        var newCanvas1 = scale(0.7, inputCanvas);

        // 返回<img> dom element
        var newCanvas2 = scale({scaleX:1.7, scaleY:1.4},
                               inputImage,
                               document.getElementById("exportCanvas2"));

        // 返回jpeg base64
        var jpegImage  = scale({width:100, height:200}, inputCanvas, 'jpeg');

        // 返回png base64
        var pngSrc     = scale(0.7, inputCanvas, 'png-src');
      })();
      </script>
    </body></html>

## Licence
MIT Licence
