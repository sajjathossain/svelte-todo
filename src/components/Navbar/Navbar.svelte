<style>
  nav {
    width: 80%;
    margin: 10px auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .links {
    display: flex;
  }

  .logo {
    font-size: 1.5rem;
    font-weight: 600;
  }

  .links > div {
    padding: 0 25px;
  }

  .links > div:hover {
    cursor: pointer;
    color: lightseagreen;
  }
</style>

<nav>
  <div class="logo">Svelte Todo App</div>
  <div class="links">
    <div>Home</div>
    <div>About</div>
    <div>Contact</div>
  </div>
</nav>
