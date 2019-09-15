<script>
  import { onMount } from "svelte";

  let popularMovies = [];

  onMount(async () => {
    const res = await fetch(
      "https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=<API_KEY>"
    );
    const json = await res.json();
    popularMovies = json.results;
  });
  console.log(popularMovies);
</script>

<slot {popularMovies} />
