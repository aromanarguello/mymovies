<script>
  import SearchForm from '../../components/SearchForm/SearchForm.svelte';

  let movies = [];
  let searchTerm = '';
  const handleFormSubmit = async () => {
    const res = await fetch(
      `https://api.themoviedb.org/3/search/movie?api_key=d3b25ee456f5215bfcc51aa849aad377&query=${searchTerm}&language=en-US`
    );
    const json = await res.json();
    movies = json.results;
    console.log(movies);
  };

  const handleSearch = ({ target: { value } }) => (searchTerm = value);
</script>

<SearchForm {handleFormSubmit} {handleSearch} />
<ul>
  {#each movies as movie}
    <li>{movie.title}</li>
  {/each}
</ul>
