<script>
  import CardDetails from './CardDetails.svelte';
  export let movie;
  let showCardFront = true;
  let movieDetail;

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
  li {
    width: 300px;
    height: 350ps;
    -webkit-box-shadow: 0px 0px 10px 3px rgba(176, 176, 176, 0.72);
    -moz-box-shadow: 0px 0px 10px 3px rgba(176, 176, 176, 0.72);
    box-shadow: 0px 0px 10px 3px rgba(176, 176, 176, 0.72);
    list-style: none;
    display: grid;
    grid-template-rows: 0.5fr 1fr;
    margin-bottom: 25px;
    border-radius: 2.5px;
  }
  .card-header {
    /* border-bottom: 1px solid lightgray; */
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  img {
    margin: 5px 0 0 0;
    width: 110px;
    height: 150px;
  }

  .card-body {
    text-align: center;
    display: grid;
    grid-template-rows: 1fr;
  }

  button {
    border: 0;
    cursor: pointer;
    background: none;
  }

  .rating-text {
    margin: 0;
  }
</style>

<li class="card-item">
  {#if showCardFront}
    <section class="card-header">
      <img
        src={`https://image.tmdb.org/t/p/w500${movie.poster_path}`}
        alt="movie-poster" />
    </section>
    <section class="card-body">
      <h2>{movie.title}</h2>
      <p class="rating-text">
        Voter Rating:
        <b>{movie.vote_average}</b>
      </p>
      <button on:click={() => toggleCard(movie.id)} class="btn-more-info">
        More info
      </button>
    </section>
  {:else}
    <CardDetails {movieDetail} {toggleCard} />
  {/if}
</li>
