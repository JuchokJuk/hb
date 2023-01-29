<script>
  import { onMount } from "svelte";
  import { fly, fade } from "svelte/transition";

  const url = "https://api.tenor.com/v1/random?q=dancing%20cat&key=LIVDSRZULELA&limit=25";
  let cats = [];

  onMount(() => {
    fetch(url)
      .then((response) => response.json())
      .then((json) => {
        cats = json.results;
      });
  });
</script>

<div class="container">
  {#each cats as cat}
    <!-- svelte-ignore a11y-missing-attribute -->
    <img
      src={cat.media[0].gif.url}
      class="cat"
      style:top={`${Math.random() * 100}%`}
      style:left={`${Math.random() * 100}%`}
      in:fly={{
        y: (Math.random() - 0.5) * 100,
        x: (Math.random() - 0.5) * 100,
        duration: 400,
        delay: 2000 + Math.random() * 2000,
      }}
      out:fade={{ duration: 400 }}
    />
  {/each}
</div>

<style>
  .container {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
  }

  .cat {
    border-radius: 4px;
    width: 100px;
    position: fixed;
  }
</style>
