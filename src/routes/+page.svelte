<script>
</script>

<head>
  <title>Puzzle Place</title>
</head>

<body>
  <main>
    <p>
      Welcome to the Puzzle Place! You can find a small variety of games and
      puzzles to play. Enjoy your time here!
    </p>
    <section>
      <h2>The Game and Puzzle List</h2>
      <p>
        Below is the list of games to play on this site. More games are coming
        soon.
      </p>
      <ul class="games-grid">
        <li class="games-grid-link">
          <a href="/">Simple Crossword</a>
        </li>
        <li class="games-grid-link">
          <a href="/2048">2048</a>
        </li>
        <li class="games-grid-link">Coming soon!</li>
        <li class="games-grid-link">Coming soon!</li>
      </ul>
    </section>
  </main>
</body>

<style>
  .games-grid {
    display: grid;
    grid-template-columns: repeat(2, 12rem);
    grid-row-gap: 1.5rem;
    grid-column-gap: 1.5rem;
    list-style-type: none;
    justify-content: center;
    align-items: center;
  }

  .games-grid-link {
    border: var(--mid);
    height: 10rem;
    width: 10rem;
    background-color: var(--mid);
    color: var(--light);
    font-size: 1rem;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .games-grid-link:hover {
    transform: scale(1.1);
  }

  .games-grid-link:hover {
    border: 1px solid var(--dark);
  }
</style>
