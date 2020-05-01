<script context="module">
	export function preload({ params, query }) {
		return this.fetch(`https://eurogroupe.org/dev/wp/wp-json/acf/v3/posts`).then(r => r.json()).then(posts => {
			return { posts };
		});
	}
</script>

<script>
	export let posts;
</script>

<style>
	.flex {
		display: flex;
	}

article{border-top:1px solid black;}
</style>

<svelte:head>
	<title>Sapper project template</title>
</svelte:head>

{#each posts as post}
		<article>
			<header>
			<div class="flex">
			<h2>{post.acf.num}</h2>
			<h2>{post.acf.title}</h2>
			<h2>{post.acf.date}</h2>
			<h2><a href='{post.acf.pdf}' target="_blank">PDF</a></h2>
			</div>
			<img src={post.acf.cover.sizes.thumbnail} width="200" alt="dg"/>
			</header>
			<div>
			{#if post.acf.image}
			<img src={post.acf.image.sizes.thumbnail} width="600" alt="dg"/>
			{/if}
			{#if post.acf.article1.title === ''}
			<div></div>
			{:else}
			<div>
				<h3>{post.acf.article1.author}</h3>
				<h3>{post.acf.article1.title}</h3>
				<a href='{post.acf.article1.pdf}' target="_blank">PDF</a>
			</div>
			{/if}
			{#if post.acf.article2.pdf === ''}
			<div></div>
			{:else}
			<div>
				<h3>{post.acf.article2.author}</h3>
				<h3>{post.acf.article2.title}</h3>
				<a href='{post.acf.article2.pdf}' target="_blank">PDF</a>
			</div>
			{/if}

{#if post.acf.article3.pdf === ''}
			<div></div>
			{:else}
			<div>
				<h3>{post.acf.article3.author}</h3>
				<h3>{post.acf.article3.title}</h3>
				<a href='{post.acf.article3.pdf}' target="_blank">PDF</a>
			</div>
			{/if}


		</div>

		</article>
	{/each}
