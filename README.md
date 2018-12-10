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
                       context.clearRect(0,0,canvas.width.height);
                       snake.x += snake.dx;
                       snake.y += snake.dy;
     //wrap snake position on edge of screen
     if (snake.x < 0) {
        snake.x = canvas.width - grid;
      }
      else if (snake.width) {
        snake.x = 0;
      }
      if (snake.y < 0) {
                      snake.y = cnavas.height) {
                      snake.y = 0;
                      }
      snake.y = 0;
      }
  // keep track of where snake has been. front of the array is always the head
  snake.cells.unshift({x: snake.x, y: snake.y});
  // remove cells as we move away from them
  if (snake.cells.length > snake.maxCells) {
    snake.cells.pop();
  }
  // draw apple
  context.fillStyle = 'pink';
  context.fillRect(apple.x, apple.y, grid-1, grid-1);
  // draw snake
  context.fillStyle = 'lightgreen';
  snake.cells.forEach(function(cell, index) {
    context.fillRect(cell.x, cell.y, grid-1, grid-1);
    // snake ate apple
    if (cell.x === apple.x && cell.y === apple.y) {
      snake.maxCells++;
      apple.x = getRandomInt(0, 25) * grid;
      apple.y = getRandomInt(0, 25) * grid;
    }
    // check collision with all cells after this one (modified bubble sort)
    for (var i = index + 1; i < snake.cells.length; i++) {
      
      // collision. reset game
      if (cell.x === snake.cells[i].x && cell.y === snake.cells[i].y) {
        snake.x = 160;
        snake.y = 160;
        snake.cells = [];
        snake.maxCells = 4;
        snake.dx = grid;
        snake.dy = 0;
        apple.x = getRandomInt(0, 25) * grid;
        apple.y = getRandomInt(0, 25) * grid;
      }
    }
  });
}
document.addEventListener('keydown', function(e) {
  // prevent snake from backtracking on itself
  if (e.which === 37 && snake.dx === 0) {
    snake.dx = -grid;
    snake.dy = 0;
  }
  else if (e.which === 38 && snake.dy === 0) {
    snake.dy = -grid;
    snake.dx = 0;
  }
  else if (e.which === 39 && snake.dx === 0) {
    snake.dx = grid;
    snake.dy = 0;
  }
  else if (e.which === 40 && snake.dy === 0) {
    snake.dy = grid;
    snake.dx = 0;
  }
});
requestAnimationFrame(loop);
</script>
</body>
</html>
