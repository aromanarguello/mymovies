<script>
  import SearchForm from '../../components/SearchForm/SearchForm.svelte';
  import Card from '../../components/Card/Card.svelte';
  import MoviesCard from '../../components/Card/MoviesCard.svelte';

  let movies = [];
  let searchTerm = '';
  const handleFormSubmit = async () => {
    const res = await fetch(
      `https://api.themoviedb.org/3/search/movie?api_key=d3b25ee456f5215bfcc51aa849aad377&query=${searchTerm}&language=en-US`
    );
    const json = await res.json();
    movies = json.results;
  };

  const handleSearch = ({ target: { value } }) => (searchTerm = value);
</script>

<style>
  li {
    list-style-type: none;
  }
</style>

<SearchForm {handleFormSubmit} {handleSearch} />
<ul>
  {#each movies as movie}
    <li>
      <Card>
        <MoviesCard {movie} />
      </Card>
    </li>
  {/each}
</ul>
