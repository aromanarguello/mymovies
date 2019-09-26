<script>
  import Card from '../../components/Card/Card.svelte';
  import Fetch from '../../components/Fetch/Fetch.svelte';

  let movieUrl =
    'https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=d3b25ee456f5215bfcc51aa849aad377';
</script>

<style>
  ul {
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
  }
</style>

<h2>Top 20 popular movies:</h2>
<Fetch let:data url={movieUrl}>
  <ul class="card-list">
    {#each data as movie}
      <Card {movie} />
    {/each}
  </ul>
</Fetch>
