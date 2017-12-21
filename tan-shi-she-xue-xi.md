```
<canvas id="can" width="400" height="400" style="background-color: black">对不起，您的浏览器不支持canvas</canvas>
<script>
  var snake = [41, 40],  //蛇身保存地址
      direction = 1,     //方向，[-1, -20, 1, 20]//cavas 400*400, 分成20*20的格子
      food = 43,         //食物位置
      speed = 500,       //速度，ms
      n,                 //蛇头下次出现位置
      ctx = document.getElementById("can").getContext("2d");

  //cavas绘制
  function draw(seat, color) {
    ctx.fillStyle = color;
    ctx.fillRect(seat % 20 * 20 + 1, ~~(seat / 20) * 20 + 1, 18, 18);
  }

  //方向改变
  document.onkeydown = function (e) {
    //ArrowLeft键值37；ArrowUp键值38；ArrowRight键值39；ArrowDown键值40
    direction = snake[1] - snake[0] === (n = [-1, -20, 1, 20][(e || event).keyCode - 37] || direction) ? direction : n;
  }

  !function () {
    snake.unshift(n = snake[0] + direction);//确定蛇头位置
    //游戏失败判断，蛇头碰到蛇身||碰到上侧壁||下侧壁||右侧||左侧
    if (snake.indexOf(n, 1) > 0 || n < 0 || n > 399 || direction === 1 && n % 20 === 0 || direction === -1 && n % 20 === 19) {
      return alert('Game Over！')
    }
    //绘制蛇首
    draw(n, "lime");
    //判断是否吃的食物，未吃到则去除蛇尾
    if (n === food) {
      while (snake.indexOf(food = ~~(Math.random() * 400)) >= 0);
      draw(food, 'yellow');
    } else {
      draw(snake.pop(), 'black');
    }
    setTimeout(arguments.callee, speed);
  }();
</script>
```



