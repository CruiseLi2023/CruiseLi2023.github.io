### The Canvas

The canvas is 400 pixels wide and 500 pixels tall. Changing the width or height changes the game area.

### The State Variables

The variables track the player's position, the block's position, the score, and whether the game is over. They are declared using `let`.

### The Game Loop

The `gameLoop()` function runs repeatedly. It draws the game, moves the block, checks collisions, and updates the score.

### Input Handling

The left and right arrow keys move the player. The event listener changes the player's X position by 20 pixels.

### Collision / Win-Lose Logic

The game checks if the player touches the falling block. If they touch, `gameOver` becomes `true`.

### Scoring

The score starts at 0. It increases by 1 whenever the block reaches the bottom and resets to the top.

### My Experiment

I changed `blockY += 3` to `blockY += 6`. The block moved faster, making the game harder.
