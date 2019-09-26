<script>
  import { Router, Route, Link } from 'svelte-routing';
  import Home from './pages/Home/Home.svelte';
  import MovieSearch from './pages/MovieSearch/MovieSearch.svelte';
  export let url = '';
</script>

<style>
  header {
    border: 1px solid red;
    text-align: center;
  }

  h1 {
    color: purple;
  }
</style>

<Router {url}>
  <header>
    <h1>MyMovies</h1>
  </header>
  <nav>
    <ul>
      <li>
        <Link to="/">Home</Link>
      </li>
      <li>
        <Link to="/search">Search</Link>
      </li>
    </ul>
  </nav>
  <main>
    <Route path="/" component={Home} />
    <Route path="/search" component={MovieSearch} />
  </main>
  <footer />
</Router>
