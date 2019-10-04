<script>
  export let movieDetail;
  export let toggleBack;
</script>

<style>
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
