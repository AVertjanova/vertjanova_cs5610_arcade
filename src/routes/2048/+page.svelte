<script>
  import Cell from "./cell.svelte";

  let board = $state([
    [0, 0, 0, 0],
    [0, 0, 2, 0],
    [0, 0, 0, 0],
    [0, 0, 0, 0],
  ]);

  function canMove(board, dir) {
    for (i of board) {
      for (j of i) {
        if (dir === "down") {
          if (board[i][j] != null && i + 1 <= 3) {
            if (board[i + 1][j] === null || board[i + 1][j] === board[i][j]) {
              return true;
            }
          }
        }
        //check right
        if (dir === "right") {
          if (board[i][j] != null && j + 1 <= 3) {
            if (board[i][j + 1] === null || board[i][j + 1] === board[i][j]) {
              return true;
            }
          }
        }
        //check up
        if (dir === "up") {
          if (board[i][j] != null && i - 1 >= 0) {
            if (board[i - 1][j] === null || board[i - 1][j] === board[i][j]) {
              return true;
            }
          }
        }
        //check left
        if (dir === "left") {
          if (board[i][j - 1] != null && j - 1 >= 0) {
            if (board[i][j - 1] === null || board[i][j - 1] === board[i][j]) {
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
        for (i = 3; i >= 0; i--) {
          for (j = 0; j <= 3; j++) {
            if (i + 1 <= 3 && board[i][j] != null) {
              if (board[i + 1][j] === null) {
                board[i + 1][j] = board[i][j];
                board[i][j] = null;
              }
              if (board[i + 1][j] === board[i][j]) {
                board[i + 1][j] = board[i + 1][j] * 2;
                board[i][j] = null;
              }
            }
          }
        }
      }
    }

    if (dir === "up") {
      while (canMove(board, dir)) {
        for (i = 0; i >= 3; i++) {
          for (j = 0; j <= 3; j++) {
            if (i - 1 >= 0 && board[i][j] != null) {
              if (board[i - 1][j] === null) {
                board[i - 1][j] = board[i][j];
                board[i][j] = null;
              }
              if (board[i - 1][j] === board[i][j]) {
                board[i - 1][j] = board[i - 1][j] * 2;
                board[i][j] = null;
              }
            }
          }
        }
      }
    }

    if (dir === "right") {
      while (canMove(board, dir)) {
        for (j = 3; j >= 0; j--) {
          for (i = 0; i <= 3; i++) {
            if (j + 1 <= 3 && board[i][j] != null) {
              if (board[i][j + 1] === null) {
                board[i][j + 1] = board[i][j];
                board[i][j] = null;
              }
              if (board[i][j + 1] === board[i][j]) {
                board[i][j + 1] = board[i][j + 1] * 2;
                board[i][j] = null;
              }
            }
          }
        }
      }
    }
    if (dir === "left") {
      while (canMove(board, dir)) {
        for (j >= 0; j <= 3; j++) {
          for (i = 0; i <= 3; i++) {
            if (j - 1 >= 0 && board[i][j] != null) {
              if (board[i][j - 1] === null) {
                board[i][j - 1] = board[i][j];
                board[i][j] = null;
              }
              if (board[i][j - 1] === board[i][j]) {
                board[i][j - 1] = board[i][j - 1] * 2;
                board[i][j] = null;
              }
            }
          }
        }
      }
    }
  }

  function handleKeyDown(event) {
    if (event.key === "ArrowDown") {
      move(board, "down");
    }
  }

  function handleKeyUp(event) {
    if (event.key === "ArrowUp") {
      move(board, "up");
    }
  }

  function handleKeyRight(event) {
    if (event.key === "ArrowDown") {
      move(board, "right");
    }
  }

  function handleKeyLeft(event) {
    if (event.key === "ArrowDown") {
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

<svelte:window onkeydown={handleKeyDown} onkeyright={handleKeyRight} />

<style>
  .board {
    display: grid;
    grid-template-columns: repeat(4, 100px);
  }
</style>
