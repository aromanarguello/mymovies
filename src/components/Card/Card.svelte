<script>
  export let movie;
  //   const { title, poster_path, vote_average } = movie;
  import { onMount } from 'svelte';
  export let eventHandler;

  // let showCardFront = true;
  const toggleCard = info => console.log(info);
  // onMount(() => {
  //   console.log(showCardFront);
  // });
</script>

<style>
  li {
    width: 300px;
    height: 300px;
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
    border-bottom: 1px solid lightgray;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  img {
    width: 50px;
    height: 150px;
  }

  .card-body-header {
    text-align: center;
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

  <section class="card-header">
    <img
      src={`https://image.tmdb.org/t/p/w500${movie.poster_path}`}
      alt="movie-poster" />
  </section>
  <section class="card-body-header">
    <h2>{movie.title}</h2>
    <p class="rating-text">
      Voter Rating:
      <b>{movie.vote_average}</b>
    </p>
    <button on:click={() => toggleCard(movie.id)} class="btn-more-info">
      More info
    </button>
  </section>

</li>
