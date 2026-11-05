<script>
  import Cell from "./cell.svelte";
  import { move } from "@avertjanova/arcade-core";
  import { canMove } from "@avertjanova/arcade-core";
  import { spawn } from "@avertjanova/arcade-core";
  import { hasMoves } from "@avertjanova/arcade-core";

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

  let startX = $state(0);
  let startY = $state(0);
  let swipeDir = $state(undefined);

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

  function catchSwipeDirection(e) {
    let dx = e.clientX - startX;
    let dy = e.clientY - startY;
    if (Math.abs(dx) > Math.abs(dy)) {
      if (dx > 0) {
        move(board, "right");
      }
      if (dx < 0) {
        move(board, "left");
      }
    } else {
      if (dy > 0) {
        move(board, "down");
      }
      if (dy < 0) {
        move(board, "up");
      }
    }
  }

  function handleKeyDown(event) {
    if (event.key === "ArrowDown") {
      move(board, "down");
      if (hasMoves(board) === false) {
        gameOver = true;
      }
    } else if (event.key === "ArrowUp") {
      move(board, "up");
      if (hasMoves(board) === false) {
        gameOver = true;
      }
    } else if (event.key === "ArrowRight") {
      move(board, "right");
      if (hasMoves(board) === false) {
        gameOver = true;
      }
    } else if (event.key === "ArrowLeft") {
      move(board, "left");
      if (hasMoves(board) === false) {
        gameOver = true;
      }
    }
  }
</script>

<div class="pageLayout">
  {#if gameOver === true}
    <h2>Game Over</h2>
  {/if}
  <div
    class="board"
    aria-label="2048 game board"
    onpointerdown={(e) => {
      startX = e.clientX;
      startY = e.clientY;
    }}
    onpointerup={(e) => {
      catchSwipeDirection(e);
    }}
  >
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

<!--  hours worked 12.5
Todo: 

Make mobile version work
fix game over
transition animations?


-->

<style>
  .board {
    display: grid;
    width: min(400px, 95%);
    aspect-ratio: 1;
    grid-template-columns: repeat(4, 1fr);
    background-color: #4b3619;
    margin: 20px;
    border-radius: 10px;
    gap: 5px;
    padding: 5px;
  }

  .pageLayout {
    display: grid;
    justify-items: center;
  }
</style>
