<script>
  import Cell from "./cell.svelte";

  let board = $state([
    [0, 0, 0, 0],
    [0, 0, 2, 0],
    [0, 0, 0, 0],
    [0, 0, 0, 0],
  ]);

  $effect(() => {
    if (curScore > highScore) {
      highScore = curScore;
    }
  });

  let curScore = $derived.by(checkScore);
  let highScore = $state(0);
  let gameOver = $state(false);

  function reset() {
    console.log("in reset function");
    board = [
      [0, 0, 0, 0],
      [0, 0, 2, 0],
      [0, 0, 0, 0],
      [0, 0, 0, 0],
    ];
    gameOver = false;
  }

  function checkScore() {
    let largest = 2;
    for (let i = 0; i < 4; i++) {
      for (let j = 0; j < 4; j++) {
        if (board[i][j] > largest) {
          largest = board[i][j];
        }
      }
    }
    return largest;
  }

  function spawn(board) {
    let randRow = Math.floor(Math.random() * 4);
    let randCol = Math.floor(Math.random() * 4);
    let placed = false;

    while (placed === false) {
      if (board[randRow][randCol] === 0) {
        placed = true;
        if ((randRow + randCol) % 2 === 0) {
          board[randRow][randCol] = 2;
        } else {
          board[randRow][randCol] = 4;
        }
      } else {
        if (hasMoves) {
          randRow = Math.floor(Math.random() * 4);
          randCol = Math.floor(Math.random() * 4);
        } else {
          placed = true;
        }
      }
    }
  }

  function canMove(board, dir) {
    for (let i = 0; i < 4; i++) {
      for (let j = 0; j < 4; j++) {
        if (dir === "down") {
          if (board[i][j] != 0 && i + 1 <= 3) {
            if (board[i + 1][j] === 0 || board[i + 1][j] === board[i][j]) {
              console.log("can move down");
              return true;
            }
          }
        }
        //check right
        if (dir === "right") {
          if (board[i][j] != 0 && j + 1 <= 3) {
            if (board[i][j + 1] === 0 || board[i][j + 1] === board[i][j]) {
              console.log("can move right");
              return true;
            }
          }
        }
        //check up
        if (dir === "up") {
          if (board[i][j] != 0 && i - 1 >= 0) {
            if (board[i - 1][j] === 0 || board[i - 1][j] === board[i][j]) {
              console.log("can move up");
              return true;
            }
          }
        }
        //check left
        if (dir === "left") {
          if (board[i][j] != 0 && j - 1 >= 0) {
            if (board[i][j - 1] === 0 || board[i][j - 1] === board[i][j]) {
              console.log("can move left");
              return true;
            }
          }
        }
      }
    }
    return false;
  }

  function hasMoves(board) {
    if (
      canMove(board, "up") ||
      canMove(board, "down") ||
      canMove(board, "left") ||
      canMove(board, "right")
    ) {
      return true;
    } else {
      return false;
    }
  }

  function move(board, dir) {
    let moved = false;
    if (dir === "down") {
      while (canMove(board, dir)) {
        for (let i = 3; i >= 0; i--) {
          for (let j = 0; j <= 3; j++) {
            if (i + 1 <= 3 && board[i][j] != 0) {
              if (board[i + 1][j] === 0) {
                board[i + 1][j] = board[i][j];
                board[i][j] = 0;
                moved = true;
              }
              if (board[i + 1][j] === board[i][j]) {
                board[i + 1][j] = board[i + 1][j] * 2;
                board[i][j] = 0;
                moved = true;
              }
            }
          }
        }
      }
    }

    if (dir === "up") {
      while (canMove(board, dir)) {
        for (let i = 0; i <= 3; i++) {
          for (let j = 0; j <= 3; j++) {
            if (i - 1 >= 0 && board[i][j] != 0) {
              if (board[i - 1][j] === 0) {
                board[i - 1][j] = board[i][j];
                board[i][j] = 0;
                moved = true;
              }
              if (board[i - 1][j] === board[i][j]) {
                board[i - 1][j] = board[i - 1][j] * 2;
                board[i][j] = 0;
                moved = true;
              }
            }
          }
        }
      }
    }

    if (dir === "right") {
      while (canMove(board, dir)) {
        for (let j = 3; j >= 0; j--) {
          for (let i = 0; i <= 3; i++) {
            if (j + 1 <= 3 && board[i][j] != 0) {
              if (board[i][j + 1] === 0) {
                board[i][j + 1] = board[i][j];
                board[i][j] = 0;
                moved = true;
              }
              if (board[i][j + 1] === board[i][j]) {
                board[i][j + 1] = board[i][j + 1] * 2;
                board[i][j] = 0;
                moved = true;
              }
            }
          }
        }
      }
    }
    if (dir === "left") {
      while (canMove(board, dir)) {
        for (let j = 0; j <= 3; j++) {
          for (let i = 0; i <= 3; i++) {
            if (j - 1 >= 0 && board[i][j] != 0) {
              if (board[i][j - 1] === 0) {
                board[i][j - 1] = board[i][j];
                board[i][j] = 0;
                moved = true;
              }
              if (board[i][j - 1] === board[i][j]) {
                board[i][j - 1] = board[i][j - 1] * 2;
                board[i][j] = 0;
                moved = true;
              }
            }
          }
        }
      }
    }
    if (moved === true) {
      spawn(board);
    }
    if (!hasMoves(board)) {
      gameOver = true;
      console.log("game over");
    }
  }

  function handleKeyDown(event) {
    if (event.key === "ArrowDown") {
      move(board, "down");
    } else if (event.key === "ArrowUp") {
      move(board, "up");
    } else if (event.key === "ArrowRight") {
      move(board, "right");
    } else if (event.key === "ArrowLeft") {
      move(board, "left");
    }
  }
</script>

<div class="pageLayout">
  {#if gameOver === true}
    <h2>Game Over</h2>
  {/if}
  <div class="board" aria-label="2048 game board">
    {#each board as row, i}
      {#each row as cellValue, j}
        <Cell value={cellValue} row={i} column={j} />
      {/each}
    {/each}
  </div>
  <button type="button" onclick={() => reset()}>New Game</button>
  <p>Current Score: {curScore}</p>
  <p>High Score: {highScore}</p>
</div>

<svelte:window onkeydown={handleKeyDown} />

<!--  hours worked 7.5 
Todo: 

Make mobile version work

transition animations?


-->

<style>
  .board {
    display: grid;
    grid-template-columns: repeat(4, max-content);
    background-color: #4b3619;
    margin: 20px;
    border-radius: 10px;
  }
  .pageLayout {
    display: grid;
    justify-content: center;
  }
</style>
