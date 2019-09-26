<script>
  import SearchForm from '../../components/SearchForm/SearchForm.svelte';

  let movies = [];
  let searchTerm = '';
  const handleFormSubmit = async () => {
    const res = await fetch(
      `https://api.themoviedb.org/3/search/movie?api_key=d3b25ee456f5215bfcc51aa849aad377&query=${searchTerm}&language=en-US`
    );
    const json = await res.json();
    movies = json;
    console.log(movies.results);
  };

  const handleSearch = ({ target: { value } }) => (searchTerm = value);
</script>

<SearchForm {handleFormSubmit} {handleSearch} />
<ul>
  {#each movies.results as movie}
    <li>{movie.title}</li>
  {/each}
</ul>
