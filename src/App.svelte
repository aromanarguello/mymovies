<script>
  import Card from "./components/Card/Card.svelte";
  import Fetch from "./components/Fetch/Fetch.svelte";
</script>

<style>
  header {
    border: 1px solid red;
    text-align: center;
  }

  h1 {
    color: purple;
  }

  ul {
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
  }
</style>

<header>
  <h1>MyMovies</h1>
</header>
<main>
  <h2>Top 20 popular movies:</h2>
  <Fetch let:popularMovies>
    <ul>
      {#each popularMovies as movie}
        {console.log(movie)}
        <Card {movie} />
      {/each}
    </ul>
  </Fetch>
</main>
<footer />
