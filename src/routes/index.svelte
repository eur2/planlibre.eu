<script context="module">
  export function preload({ params, query }) {
    return this.fetch(`https://eurogroupe.org/dev/wp/wp-json/wp/v2/posts`)
      .then((r) => r.json())
      .then((posts) => {
        return { posts };
      });
  }
</script>

<script>
  export let posts;
  import Article from "../components/Article.svelte";
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
</script>
<div class="sticky t0 p0111 bg-white flex jc-sb">
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
</div>
{#each filteredPosts as post}
<Article
  num="{post.acf.num}"
  title="{post.acf.title}"
  date="{post.acf.date}"
  pdf="{post.acf.pdf}"
  cover="{post.acf.cover.sizes.thumbnail}"
>
  <div class="content flex">
    {#if post.acf.image}
    <div class="p flex jc-center">
      <img src="{post.acf.image.sizes.medium}" width="800" alt="dg" />
    </div>
    {/if}
    <div class="p flex wrap jc-sa">
     {#if post.acf.article1.title === ''}
    <div></div>
    {:else}
    <div class="p">
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
    <div class="p">
      <a href="{post.acf.article1.pdf}" rel="noopener" target="_blank">
        <div class="center">
          <h4>{post.acf.article1.author}</h4>
          <h3>{post.acf.article1.title}</h3>
        </div>
      </a>
    </div>
    {/if} {#if post.acf.article3.title === ''}
    <div></div>
    {:else}
    <div class="p">
      <a href="{post.acf.article1.pdf}" rel="noopener" target="_blank">
        <div class="center">
          <h4>{post.acf.article1.author}</h4>
          <h3>{post.acf.article1.title}</h3>
        </div>
      </a>
    </div>
    {/if} {#if post.acf.article4.title === ''}
    <div></div>
    {:else}
    <div class="p">
      <a href="{post.acf.article1.pdf}" rel="noopener" target="_blank">
        <div class="center">
          <h4>{post.acf.article1.author}</h4>
          <h3>{post.acf.article1.title}</h3>
        </div>
      </a>
    </div>
    {/if}
  </div>
</Article>
{/each}
