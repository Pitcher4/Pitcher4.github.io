---
title: "Ping Pong Game"
date: 2023-01-08T17:10:22Z
draft: false
---

# Write Up
This game has a platform at the bottom of the screen that the user controls. There is as ball that bounces on the edges of the screen and block sthat the user has to destroy. The users score and life count shows at the middle of the screen. 



The player starts with three lives. When they have no lifes left, an alert will output "Game over".



When the user destroys all the blocks, an alert will output "You won!"



# Implementation
I used JavaScript for this project. I started by making the ball variables. The ball has an x variable, a y variable, an x ball velocity variable and a y ball velocity variable. 

Then I did the same with the platform.

### The Platform
First I made leftPressed (meaning left arrow key pressed) equal false. Then I inputed when the left key is pressed, it equals true. I did this for the right arrow key aswell. 

### The Ball
Firstly I made a function called "draw ball" which colours the ball in the colour I chose (red). 
# Code
## script.js
```JavaScript
let canvas = document.getElementById('myCanvas');
let ctx = canvas.getContext('2d');
let lives = 3;
let score = 0;
let xBall = 300;
let yBall = 300;
let xBallVel = 3;
let yBallVel = 3;
let xRect = canvas.width / 2;
let yRect = canvas.height - 40;
let yRectVel = -0;
let xRectVel = 0;
let rightPressed = false;
let leftPressed = false;
let blocks = [];
for (let j = 0; j < 3; j++) {
	blocks[j] = [];
	for (let i = 0; i < 10; i++) {
		let xBlock = i * 70 + 30;
		let yBlock = j * 40 + 20;
		let block = {
			x: xBlock,
			y: yBlock
		};
		blocks[j][i] = block;
	}
}
function drawText(text, x, y, colour) {
	ctx.font = '20px Arial';
	ctx.fillStyle = colour;
	ctx.fillText(text, x, y);
}
function drawBlocks() {
	for (let j = 0; j < 3; j++) {
		for (let i = 0; i < 10; i++) {
			if (blocks[j][i]) {
				ctx.beginPath();
				ctx.rect(blocks[j][i].x, blocks[j][i].y, 40, 20);
				ctx.fillStyle = 'blue';
				ctx.fill();
				ctx.closePath();
			}
		}
	}
}
function drawRect() {
	ctx.beginPath();
	ctx.rect(xRect, yRect, 120, 22);
	ctx.fillStyle = 'blue';
	ctx.fill();
	ctx.closePath();
}
function drawBall() {
	ctx.beginPath();
	ctx.arc(xBall, yBall, 20, 0, 2 * Math.PI);
	ctx.fillStyle = 'red';
	ctx.fill();
	ctx.closePath();
}
function keyDown(event) {
	if (event.key == 'ArrowRight') {
		rightPressed = true;
	} else if (event.key == 'ArrowLeft') {
		leftPressed = true;
	}
}
function keyUp(event) {
	if (event.key == 'ArrowRight') {
		rightPressed = false;
	} else if (event.key == 'ArrowLeft') {
		leftPressed = false;
	}
}
function draw() {
	ctx.clearRect(0, 0, canvas.width, canvas.height);
	drawBall();
	drawRect();
	drawBlocks();
	drawText('Score: ' + score, 300, 200, 'blue');
	drawText('Lives: ' + lives, 400, 200, 'red');
}
function blockCollisionDetection() {
	for (let j = 0; j < 3; j++) {
		for (let i = 0; i < 10; i++) {
			if (blocks[j][i]) {
				const block = blocks[j][i];
				if (xBall > block.x && xBall < block.x + 70 && yBall > block.y && yBall < block.y + 40) {
					blocks[j][i] = null;
					score++;
					yBallVel *= -1;
					if (score == 30) {
						alert('You won!');
						document.location.reload();
						clearInterval(interval);
					}
				}
			}
		}
	}
}
function update() {
	//update ball
	if (yBall > canvas.height) {
		lives--;
		if (lives == 0) {
			alert('Game over');
			document.location.reload();
			clearInterval(interval);
		} else {
			xBall = 360;
			yBall = 400;
			xBallVel = 2;
			yBallVel = -2;
		}
	}
	if (xBall > canvas.width) {
		xBallVel *= -1;
	}
	if (xBall < 0) {
		xBallVel *= -1;
	}
	if (yBall < 0) {
		yBallVel *= -1;
	}
	if (xBall > xRect && xBall < xRect + 120 && yBall > yRect && yBall < yRect + 20) {
		yBallVel *= -1;
	}
	xBall += xBallVel;
	yBall += yBallVel;
	//update rectangle/paddle (rect.)
	if (rightPressed) {
		xRectVel = 3;
	} else if (leftPressed) {
		xRectVel = -3;
	} else {
		xRectVel = 0;
	}
	xRect += xRectVel;
	yRect += yRectVel;
	blockCollisionDetection();
}
function loop() {
	draw();
	update();
}
document.addEventListener('keydown', keyDown, false);
document.addEventListener('keyup', keyUp, false);
let interval = setInterval(loop, 10);
```

## index.html
```html
<html>
	<head>
		<title>Javascript Game</title>
		<link rel="stylesheet" href="styles.css">
	</head>
	<body>
		<canvas id="myCanvas" width="720" height="480"></canvas>
		<script src="script.js"></script>
	</body>
</html>
```

## styles.css
```css
canvas {
  background-color: #eee;
  margin: 0 auto;
  display: block;
}
```