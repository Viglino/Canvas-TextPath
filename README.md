# [Canvas-TextPath](https://github.com/Viglino/Canvas-TextPath/

Adds extra functionality to the CanvasRenderingContext2D to draw text along a path.
Check out the [demo](https://viglino.github.io/Canvas-TextPath/)!

## How it runs?

As SVG does support text along paths, canvas doesn't have such native support. 
This contribution tries to fill the lack and gives you a textPath function to use with a CanvasRenderingContext2D.
The method writes one character at a time rotated and scaled according to the path.

NOTE: this extends the CanvasRenderingContext2D prototype. 
It adds a `textPath` function to draw text along a list of coordinates.
It adds `textOverflow`, `textJustify` and `textStrokeMin` properties to CanvasRenderingContext2D.

It support native options include text alignment (left, center and right) and baseline positionning.
Stroke an fill is done in one pass for performance purpose.


## Usage

Include the following files in your page:
```html
<script type="text/javascript" src="https://cdn.rawgit.com/Viglino/Canvas-TextPath/master/ctxtextpath.js"></script> 
```
Add a canvas on your page
```html
<canvas id="myCanvas" width="200" height="100"></canvas> 
```
Then begin to draw in the canvas
```javascript
window.onload = function() {
  var c = document.getElementById("myCanvas");
  var ctx = c.getContext("2d");
  ctx.font = "30px Arial";
  ctx.txtAlign = "center";
  ctx.textPath ("Hello world", [10,60, 100,40, 190,60]);
}
</script>
```
The path is an Array of coordinates x1,y1, x2, y2, etc.


## License

[MIT License](https://github.com/lukehaas/css-loaders/blob/step2/LICENSE)
