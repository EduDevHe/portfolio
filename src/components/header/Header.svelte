<header class="header">
  <nav>
    <div>
      <a href="/">Home</a>
      <a href="/">About</a>
      <a href="/">Contact</a>
      <a href="/">Blog</a>
    </div>
  </nav>
</header>

<style>
  .header {
    width: 100%;
    display: flex;
    justify-content: end;
    min-height: 3rem;
    border: 2px solid pink;
  }

  nav {
    min-width: 50%;
    width: 50%;
    height: 100%;
    padding: 1rem;

    display: flex;
    align-items: center;
    flex-direction: row;
    justify-content: center;
    border: 1px solid blue;
  }

  div {
    height: 100%;
    min-width: fit-content;
    border: 1px solid green;

    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    gap: 0.5rem;
  }

  a {
    padding: 1rem;
  }
</style>
