<script>
  export let movie;
  console.log(movie);
</script>

<style>
  li {
    width: 300px;
    height: 300px;
    border: 1px solid purple;
    list-style: none;
    display: grid;
    grid-template-rows: 0.5fr 1fr;
  }
  .card-header {
    border: 2px solid green;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  img {
    width: 130px;
    height: 130px;
  }
</style>

<li class="card-item">
  <section class="card-header">
    <img
      src={`https://image.tmdb.org/t/p/w500${movie.poster_path}`}
      alt="movie-poster" />
  </section>
  <section>
    <h2>{movie.title}</h2>
  </section>
</li>
