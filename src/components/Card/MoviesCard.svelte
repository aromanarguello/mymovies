<script>
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

  const toggleBack = () => (showCardFront = !showCardFront);
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

  button {
    border: 0;
    cursor: pointer;
    background: none;
  }

  p {
    margin: 0 0 3px 10px;
  }

  .movie-overview {
    margin: 10px 0 10px 10px;
    height: 130px;
    overflow-y: scroll;
  }

  section {
    margin: 10px 0 0 0;
  }
</style>

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
  <section>
    <p>
      <strong>Genres:</strong>
      {movieDetail.genres.map(({ name }) => name)}
    </p>
    <p>
      <strong>Release date:</strong>
      {movieDetail.release_date}
    </p>
    <p>
      <strong>Status:</strong>
      {movieDetail.status}
    </p>
    <p>
      <strong>Rating:</strong>
      {movieDetail.vote_average}
    </p>
    <p>
      <strong>Runtime:</strong>
      {movieDetail.runtime} mins
    </p>
  </section>
  <p class="movie-overview">{movieDetail.overview}</p>
  <button on:click={() => toggleBack()} class="btn-more-info">Back</button>
{/if}
