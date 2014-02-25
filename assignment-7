<!doctype html>
<html>
<head>
	<title>Paint Shop</title>
	<meta charset="utf-8">
	<style>
canvas { display: block; }
	</style>
</head>
<body>

	<button class="shape" data-shape="square">[]</button>
	<button class="shape" data-shape="circle">O</button>
	<button class="shape" data-shape="white">Clear</button>

	<button class="size" data-size="10">Small</button>
	<button class="size" data-size="30">Large</button>

	<button class="color" data-color="red">Red</button>
	<button class="color" data-color="blue">Blue</button>
	<button class="color" data-color="pink">Pink</button>
	<button class="color" data-color="orange">Orange</button>

	/*
	<button class="clear" data-clear="white">Clear</button>
	*/

	<canvas id="canvas" width=800 height=600></canvas>

<script src="http://code.jquery.com/jquery-2.1.0.min.js"></script>
<script>

var canvas = document.getElementById("canvas");
var context = canvas.getContext("2d");

var $canvas = $(canvas);

var brush = {
	active: false,
	shape: "square",
	size: 20,
	color: "red"
};

var drawRect = function(x, y, size) {
	context.fillRect(x - size / 2, y - size / 2, size, size);
};

var drawCircle = function(x, y, size) {
	context.beginPath();
	context.arc(x, y, size / 2, 0, 2 * Math.PI);
	context.fill();
};

var clearDraw = function(x, y, size) {
	context.beginPath();
	context.clearRect(x - size / 2, y - size / 2, size, size);
	context.fill();
};

//basic mouseover interaction
$canvas.on("mousemove", function(e) {
	//adjust for canvas position on page
	var offset = $canvas.offset();
	var x = e.pageX - offset.left;
	var y = e.pageY - offset.top;
	//only draw if brush is active
	if (brush.active) {
		context.fillStyle = brush.color;
		if (brush.shape == "circle") {
			drawCircle(x, y, brush.size);
		} else if (brush.shape == "square") {
			drawRect(x, y, brush.size);
		} else if (brush.shape == "white") {
			clearDraw(x, y, brush.size);
		/*} else if (brush.shape == "white") {
			clearDraw(x, y, brush.size);
		*/
	}
});

$canvas.on("mousedown mouseup", function(e) {
	// if (e.type == "mousedown") {
	// 	brush.active = true;
	// } else {
	// 	brush.active = false;
	// }
	brush.active = e.type == "mousedown";
});

var shapes = $(".shape");
shapes.on("click", function(e) {
	var $this = $(this);
	var shape = $this.attr("data-shape");
	brush.shape = shape;
});

var sizes = $(".size");
sizes.on("click", function() {
	var $this = $(this);
	var size = $this.attr("data-size");
	brush.size = size;
});

var colors = $(".color");
colors.on("click", function() {
	var $this = $(this);
	var color = $this.attr("data-color");
	brush.color = color;
});

/*var clears = $(".clear");
clears.on("click", function() {
	var $this = $(this);
	var clear = $this.attr("data-clear");
	brush.clear = clear;
});
*/

</script>
</body>
</html>
