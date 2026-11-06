<script>
  import { resolve } from "$app/paths";
</script>

<nav class="navbar">
  <header class="logo">
    <h1>Puzzle Place</h1>
  </header>
  <ul class="nav-link-list">
    <li>
      <a class="nav-link" href={resolve("/")}>Games</a>
    </li>
    <li>
      <a class="nav-link" href={resolve("/about")}>About</a>
    </li>
    <li><a class="nav-link" href={resolve("/contact")}>Contact</a></li>
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
    text-decoration: none;
    line-height: 1.1;
  }

  .nav-link-list {
    display: flex;
    list-style-type: none;
    align-items: baseline;
    padding: 0;
    margin: 0;
    gap: 1rem;
    padding-right: 20px;
  }

  .nav-link {
    color: var(--dark);
    font-weight: bold;
  }

  @media (max-width: 500px) {
    .nav-link-list {
      flex-direction: column;
      gap: 0.3rem;
    }
    .navbar {
      position: static;
    }
    .logo {
      padding-left: 10px;
    }
  }

  .nav-link:hover,
  .nav-link:focus-visible {
    color: var(--light);
  }
</style>
