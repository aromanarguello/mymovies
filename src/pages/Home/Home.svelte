<script>
  import Card from '../../components/Card/Card.svelte';
  import Fetch from '../../components/Fetch/Fetch.svelte';
  import CardDetails from '../../components/Card/CardDetails.svelte';
  import CardFront from '../../components/Card/CardFront.svelte';
  let movieUrl =
    'https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=d3b25ee456f5215bfcc51aa849aad377';

  let showCardFront = true;
  let movieDetail;

  const toggleBack = () => (showCardFront = !showCardFront);

  const toggleCard = async info => {
    if (!info) {
      showCardFront = !showCardFront;
      return;
    }
    const res = await fetch(
      `https://api.themoviedb.org/3/movie/${info}?api_key=d3b25ee456f5215bfcc51aa849aad377`
    );
    const json = await res.json();
    movieDetail = json;
    showCardFront = !showCardFront;
  };
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
      <Card>
        {#if showCardFront}
          <CardFront {toggleCard} {movie} />
        {:else}
          <CardDetails {toggleBack} {movieDetail} />
        {/if}
      </Card>
    {/each}
  </ul>
</Fetch>
