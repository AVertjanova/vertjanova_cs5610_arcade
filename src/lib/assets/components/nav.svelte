<nav class="navbar">
  <div>this is the navbar</div>
  <header class="logo">
    <a class="logo" href="/"><h1>Puzzle Place</h1></a>
  </header>
  <ul class="nav-link-list">
    <li>
      <a class="cur-nav-link" href="/crossword">Crossword</a>
    </li>
    <li>
      <a class="nav-link" href="/about">About</a>
    </li>
    <li><a class="nav-link" href="/contact">Contact</a></li>
  </ul>
</nav>

<style>
  .navbar {
    background-color: var(--mid);
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: sticky;
    top: 0;
  }

  .logo {
    color: var(--light);
    padding-left: 20px;
  }

  .nav-link-list {
    display: flex;
    list-style-type: none;
    padding: 0;
    margin: 0;
    gap: 1rem;
    padding-right: 20px;
  }

  .nav-link {
    color: var(--dark);
    font-weight: bold;
  }

  .cur-nav-link {
    color: var(--light);
    font-weight: bold;
  }

  .nav-link:hover,
  .nav-link:focus-visible {
    color: var(--light);
  }
</style>
