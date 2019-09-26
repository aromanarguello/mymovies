<script>
  let searchTerm = undefined;

  export let handleFormSubmit;
  export let handleSearch;
</script>

<form on:submit|preventDefault={() => handleFormSubmit()}>
  <label for="movie-search">Search movie:</label>
  <input
    type="text"
    name="movie-search"
    on:change={e => handleSearch(e)}
    id="movie-search" />
  <button type="submit">Search</button>
</form>
