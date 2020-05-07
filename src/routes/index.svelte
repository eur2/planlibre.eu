<script context="module">
  //https://pl.maop.fr/wp-json/wp/v2/posts?custom_per_page=200
  export function preload({ params, query }) {
    return this.fetch(`https://pl.maop.fr/wp-json/wp/v2/posts`)
      .then((r) => r.json())
      .then((posts) => {
        return { posts };
      });
  }
</script>

<script>
  export let posts;
  import Front from "../components/Front.svelte";
  import Post from "../components/Post.svelte";

  let searchTerm = "";
  $: filteredPosts = posts.filter(
    (post) =>
      post.acf.num.toLowerCase().indexOf(searchTerm) !== -1 ||
      post.acf.date.toLowerCase().indexOf(searchTerm) !== -1 ||
      post.acf.title.toLowerCase().indexOf(searchTerm) !== -1 ||
      post.acf.article1.author.toLowerCase().indexOf(searchTerm) !== -1 ||
      post.acf.article1.title.toLowerCase().indexOf(searchTerm) !== -1 ||
      post.acf.article2.author.toLowerCase().indexOf(searchTerm) !== -1 ||
      post.acf.article2.title.toLowerCase().indexOf(searchTerm) !== -1 ||
      post.acf.article3.author.toLowerCase().indexOf(searchTerm) !== -1 ||
      post.acf.article3.title.toLowerCase().indexOf(searchTerm) !== -1 ||
      post.acf.article4.author.toLowerCase().indexOf(searchTerm) !== -1 ||
      post.acf.article4.title.toLowerCase().indexOf(searchTerm) !== -1
  );
  // import { onMount } from "svelte";
  // onMount(() => {
  $: randomPost = posts[Math.floor(Math.random() * 20 )];
</script>
<Front>
    {#if randomPost && randomPost.acf.image}
    <img src="{randomPost.acf.image.sizes.large}" width="800" alt="plan libre" />
{/if}
</Front>
<nav class="sticky t0 p251251 bg-white flex jc-sb">
<form role="search">
  <input
    type="text"
    name="search"
    aria-label="Search"
    placeholder="Recherche"
    bind:value="{searchTerm}"
  />
</form>
<a href="https://www.instagram.com/plan_libre/" rel="noopener" target="_blank">Instagram</a>
</nav>
<main>
{#each filteredPosts as post}
<Post
  num="{post.acf.num}"
  title="{post.acf.title}"
  date="{post.acf.date}"
  pdf="{post.acf.pdf}"
  cover="{post.acf.cover.sizes.thumbnail}"
>
  <div class="content flex">
    {#if post.acf.image}
    <div class="p flex jc-center flex50">
      <img src="{post.acf.image.sizes.large}" alt="plan libre" />
    </div>
    {/if}
    <div class="p flex wrap jc-sa flex50">
     {#if post.acf.article1.title === ''}
    <div></div>
    {:else}
    <div class="p flex50 article">
      <a href="{post.acf.article1.pdf}" rel="noopener" target="_blank">
        <div class="center">
          <h4>{post.acf.article1.author}</h4>
          <h3>{post.acf.article1.title}</h3>
        </div>
      </a>
    </div>
    {/if} {#if post.acf.article2.title === ''}
    <div></div>
    {:else}
    <div class="p flex50 article">
      <a href="{post.acf.article2.pdf}" rel="noopener" target="_blank">
        <div class="center">
          <h4>{post.acf.article2.author}</h4>
          <h3>{post.acf.article2.title}</h3>
        </div>
      </a>
    </div>
    {/if} {#if post.acf.article3.title === ''}
    <div></div>
    {:else}
    <div class="p flex50 article">
      <a href="{post.acf.article3.pdf}" rel="noopener" target="_blank">
        <div class="center">
          <h4>{post.acf.article3.author}</h4>
          <h3>{post.acf.article3.title}</h3>
        </div>
      </a>
    </div>
    {/if} {#if post.acf.article4.title === ''}
    <div></div>
    {:else}
    <div class="p flex50 article">
      <a href="{post.acf.article4.pdf}" rel="noopener" target="_blank">
        <div class="center">
          <h4>{post.acf.article4.author}</h4>
          <h3>{post.acf.article4.title}</h3>
        </div>
      </a>
    </div>
    {/if}
  </div>
</Post>
{/each}
</main>
