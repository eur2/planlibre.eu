<script context="module">
  export function preload({ params, query }) {
    return this.fetch(`https://eurogroupe.org/dev/wp/wp-json/wp/v2/pages`)
      .then((r) => r.json())
      .then((posts) => {
        return { posts };
      });
  }
</script>

<script>
  import Subscribe from "../components/Subscribe.svelte";

  // import Nav from '../components/Nav.svelte';
  // export let segment;
  export let posts;
</script>

<style>
  /* main {
		position: relative;
		max-width: 56em;
		background-color: white;
		padding: 2em;
		margin: 0 auto;
		box-sizing: border-box;
	} */
</style>

<!-- <Nav {segment}/> -->
<header>
  {#each posts as post} {#if post.slug === 'header'}
  <div>
    {@html post.content.rendered}
  </div>
  {/if} {/each}
</header>
<main>
  <slot></slot>
</main>

{#each posts as post} {#if post.slug === 'subscribe'}
<Subscribe>
  {@html post.content.rendered}
</Subscribe>
{/if} {/each}
