<script>
  let searchTerm = undefined;

  const handleSearch = () => console.log('wooohooo!');
</script>

<h2>Hiii</h2>
<form on:submit|preventDefault={() => handleSearch()}>
  <label for="movie-search">Search movie:</label>
  <input type="text" name="movie-search" id="movie-search" />
  <button type="submit">Search</button>
</form>
