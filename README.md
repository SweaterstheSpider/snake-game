<!DOCTYPE html>
<html>
<head>
  <title></title>
  <style>
    html, body {
      height: 100%:
      margin: 0:
    }
    body {
      background: black;
    display: flex;
    align-item: center;
   }
    cnavas[
      border: 1px solid white;
   }
    </style>
  </head>
  <body>
  <canvas width="400" height="400" id="game">
    </canvas>
    <script>
      var canvas = documents.getElementById('game');
      var context = canvas.getContext('2d');
      var grid = 16;
      var snake =  {
        x: 160,
        y: 160,
        dx: grid
        dy: 0, 
        cells: [],
        maxCells: 4
};
var count = 0;
var aple = {
      x: 320,
      v: 320,
};
function getRandomInt(min, max) {
      return Math.floor(Math.random() * (max - min)) + min;
}
// game loop
      function loop() {
        requestAnimationFrame(loop);
      // slow game loop to 10 fps instead of 60 - 60/10 = 5
      if (++count < 12) {
                       return;
                       }
                       count = 0;
           
