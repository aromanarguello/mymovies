<script>
  export let movie;
  export let toggleCard;
  let movieDetail;
</script>

<style>
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
