<script>
  import Cell from "./cell.svelte";

  let board = $state([
    [0, 0, 0, 0],
    [0, 0, 2, 0],
    [0, 0, 0, 0],
    [0, 0, 0, 0],
  ]);

  function canMove(board, dir) {
    for (let i = 0; i < 4; i++) {
      for (let j = 0; j < 4; j++) {
        if (dir === "down") {
          if (board[i][j] != 0 && i + 1 <= 3) {
            if (board[i + 1][j] === 0 || board[i + 1][j] === board[i][j]) {
              return true;
            }
          }
        }
        //check right
        if (dir === "right") {
          if (board[i][j] != 0 && j + 1 <= 3) {
            if (board[i][j + 1] === 0 || board[i][j + 1] === board[i][j]) {
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
      canMove(board, up) ||
      canMove(board, down) ||
      canMove(board, left) ||
      canMove(board, right)
    ) {
      return true;
    } else {
      return false;
    }
  }

  function move(board, dir) {
    if (dir === "down") {
      while (canMove(board, dir)) {
        for (let i = 3; i >= 0; i--) {
          for (let j = 0; j <= 3; j++) {
            if (i + 1 <= 3 && board[i][j] != 0) {
              if (board[i + 1][j] === 0) {
                board[i + 1][j] = board[i][j];
                board[i][j] = 0;
              }
              if (board[i + 1][j] === board[i][j]) {
                board[i + 1][j] = board[i + 1][j] * 2;
                board[i][j] = 0;
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
              }
              if (board[i - 1][j] === board[i][j]) {
                board[i - 1][j] = board[i - 1][j] * 2;
                board[i][j] = 0;
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
              }
              if (board[i][j + 1] === board[i][j]) {
                board[i][j + 1] = board[i][j + 1] * 2;
                board[i][j] = 0;
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
              }
              if (board[i][j - 1] === board[i][j]) {
                board[i][j - 1] = board[i][j - 1] * 2;
                board[i][j] = 0;
              }
            }
          }
        }
      }
    }
  }

  function handleKeyDown(event) {
    if (event.key === "ArrowDown") {
      console.log("down");
      move(board, "down");
    } else if (event.key === "ArrowUp") {
      console.log("up");
      move(board, "up");
    } else if (event.key === "ArrowRight") {
      console.log("right");
      move(board, "right");
    } else if (event.key === "ArrowLeft") {
      console.log("left");
      move(board, "left");
    }
  }

  function handleKeyRight(event) {
    if (event.key === "ArrowRight") {
      console.log("right");
      move(board, "right");
    }
  }

  function handleKeyLeft(event) {
    if (event.key === "ArrowLeft") {
      console.log("left");
      move(board, "left");
    }
  }
</script>

<div class="board">
  {#each board as row, i}
    {#each row as cellValue, j}
      <Cell value={cellValue} row={i} column={j} />
    {/each}
  {/each}
</div>

<svelte:window onkeydown={handleKeyDown} />

// hours worked 4

<style>
  .board {
    display: grid;
    grid-template-columns: repeat(4, 100px);
  }
</style>
