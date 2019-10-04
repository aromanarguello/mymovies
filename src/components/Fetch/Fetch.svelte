<script>
  import { onMount } from 'svelte';
  export let url;
  let data = [];

  onMount(async () => {
    const res = await fetch(url);
    const json = await res.json();
    data = json.results;
  });

  console.log(data);
</script>

<slot {data} />
