# [Canvas-TextPath](https://github.com/Viglino/Canvas-TextPath/)

Adds extra functionality to the CanvasRenderingContext2D to draw text along a path.

Check out the [demo](https://viglino.github.io/Canvas-TextPath/)!

## How it runs?

As SVG does support text along paths, canvas doesn't have such native support. 
This contribution tries to fill the lack and gives you a `textPath` function to use with a CanvasRenderingContext2D.
The method writes one character at a time rotated and scaled according to the path.

NOTE: this extends the CanvasRenderingContext2D prototype. 
It adds a `textPath` function to draw text along a path (as an Array of coordinates).
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
  
  // Draw support path
  ctx.strokeStyle = "red";
  ctx.lineWidth=2;
  ctx.moveTo(10,60);
  ctx.lineTo(100,40);
  ctx.lineTo(190,60);
  ctx.stroke();
  
  // Render text
  ctx.font = "24px Arial";
  ctx.textAlign = "center";
  ctx.textBaseline = "middle";
  ctx.lineWidth = 0.01;     // No outline
  ctx.textPath ("Hello world", [10,60, 100,40, 190,60]);
}
</script>
```
The path is an Array of coordinates [x1,y1, x2, y2, etc.]

## Properties

Extra properties are added to the CanvasRenderingContext2D.

* `textOverflow` string: specifies what happens if text overflows the path, default "" (means hidden). Possible values are 'visible' to show the text, 'ellipsis' to show "..." or a string that will be displayed at the end of the truncated text. Use "" to hide overflow content.
* `textJustify` boolean: true for justifying text, defaul false. If false, take the textAlign propertie to align text.
* `textStrokeMin` number: the minimum size (in pixel) of the path underneath the text is not displayed.

If you specify a `lineWitdth` less than 0.1 no stroke is drawn. Use a `fillStyle` as 'transparent' to not fill the text

```javascript
  ctx.textOverflow = "ellipsis";
  ctx.textJustify = true;
  ctx.textStrokeMin = 40;
  ctx.textPath ("Hello world", [10,60, 100,40, 190,60]);
```


## License

[MIT License](https://github.com/lukehaas/css-loaders/blob/step2/LICENSE)
