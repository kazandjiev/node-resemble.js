resemblejs-tolerance
================

Analyse and compare images with Javascript. This project does not need canvas or any other binary denpendencies.
It is a modification of [node-resemble-js](https://github.com/lksv/node-resemble.js)


### Get it

`npm install node-resemble-js`

### Example

Retrieve basic analysis on image.

```javascript
var api = resemble(fileData).onComplete(function(data){
	console.log(data);
	/*
	{
	  red: 255,
	  green: 255,
	  blue: 255,
	  brightness: 255
	}
	*/
});
```

Use resemble to compare two images.

```javascript
var diff = resemble(file).compareTo(file2).ignoreColors().onComplete(function(data){
	console.log(data);
	/*
	{
	  misMatchPercentage : 100, // %
	  isSameDimensions: true, // or false
	  dimensionDifference: { width: 0, height: -1 }, // defined if dimensions are not the same
	  getImageDataUrl: function(){}
	}
	*/
});
```

You can also change the comparison method after the first analysis.

```javascript
	var tolerance = { // between 0 and 255
		red: 16,
		green: 16,
		blue: 16,
		alpha: 16,
		minBrightness: 16,
		maxBrightness: 240
	};
// diff.setTolerance(tolerance);
// diff.ignoreColors();
// diff.ignoreAntialiasing();

```

And change the output display style.

```javascript
resemble.outputSettings({
  errorColor: {
    red: 255,
    green: 0,
    blue: 255
  },
  errorType: 'movement',
  transparency: 0.3
});
// resembleControl.repaint();
```

--------------------------------------

Credits:
 * Created by [James Cryer](http://github.com/jamescryer) and the Huddle development team.
 * [Lukas Svoboda](http://github.com/lksv) - modification for node.js
 * [Ivan Kazandzhiev](http://github.com/kazandjiev) - exposing tolerance for public modification
