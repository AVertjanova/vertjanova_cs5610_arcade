<script>
  import { resolve } from "$app/paths";
</script>

<head>
  <title>Puzzle Place</title>
</head>

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
        <a href={resolve("/crossword")}>Simple Crossword</a>
      </li>
      <li class="games-grid-link">
        <a href={resolve("/2048")}>2048</a>
      </li>
      <li class="games-grid-link">Coming soon!</li>
      <li class="games-grid-link">Coming soon!</li>
    </ul>
  </section>
</main>

<style>
  .games-grid {
    display: grid;
    width: min(400px, 95%);
    grid-template-columns: repeat(2, 1fr);
    grid-row-gap: 1.5rem;
    grid-column-gap: 1.5rem;
    list-style-type: none;
    justify-content: center;
    align-items: center;
    padding: 0px;
    margin-inline: auto;
  }

  .games-grid-link {
    border: var(--mid);
    width: 100%;
    aspect-ratio: 1;
    background-color: var(--mid);
    color: var(--light);
    font-size: 1rem;
    display: flex;
    justify-content: center;
    align-items: center;
    box-sizing: border-box;
  }

  .games-grid-link:hover {
    transform: scale(1.1);
  }

  .games-grid-link:hover {
    border: 1px solid var(--dark);
  }
</style>
