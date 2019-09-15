<script>
  import { onMount } from "svelte";
  export let url;
  let popularMovies = [];

  onMount(async () => {
    const res = await fetch(url);
    const json = await res.json();
    popularMovies = json.results;
  });
</script>

<slot {popularMovies} />
