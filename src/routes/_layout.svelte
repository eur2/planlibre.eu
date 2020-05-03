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
  import Header from "../components/Header.svelte";
  import Subscribe from "../components/Subscribe.svelte";
  import Logo from "../components/Logo.svelte";
  export let posts;
</script>
<svelte:head>
  <title>Plan Libre - Journal de la Maison de l'Architecture Occitanie-Pyrénées</title>
  <meta name="description" content="Journal de la Maison de l'Architecture Occitanie-Pyrénées" />
      <meta name="og:title" content="Plan Libre" />
      <meta name="og:description" content="Journal de la Maison de l'Architecture Occitanie-Pyrénées" />
      <meta name="og:type" content="website" />
      <meta name="og:image" content="favicon.png" />
      <meta name="twitter:card" content="summary" />
      <meta name="twitter:title" content="Plan Libre" />
      <meta name="twitter:description" content="Journal de la Maison de l'Architecture Occitanie-Pyrénées" />
      <meta name="twitter:image" content="favicon.png" />
</svelte:head>

<Header>
  {#each posts as post} {#if post.slug === 'header'} {@html
  post.content.rendered} {/if} {/each}
</Header>
<main>
  <slot></slot>
  <Logo/>
</main>

{#each posts as post} {#if post.slug === 'subscribe'}
<Subscribe>
  {@html post.content.rendered}
</Subscribe>
{/if} {/each}
