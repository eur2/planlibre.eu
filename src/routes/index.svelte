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
</style>

<svelte:head>
	<title>Sapper project template</title>
</svelte:head>

{#each posts as post}
		<article>
			<header>
			<div class="flex">
			<h2>{post.acf.date}</h2>
			<a href='{post.acf.pdf}' target="_blank">PDF</a>
			</div>
			<img src={post.acf.couverture.sizes.thumbnail} width="200" alt="dg"/>
			</header>
			<div>
			{#if post.acf.image}
			<img src={post.acf.image.sizes.thumbnail} alt="dg"/>
			{/if}
			{#if post.acf.article1.pdf === false}
			<div></div>
			{:else}
			<div>
				<h2>{post.acf.article1.titre}</h2>
				<a href='{post.acf.article1.pdf}' target="_blank">PDF</a>
			</div>
			{/if}
			{#if post.acf.article2.pdf === false}
			<div></div>
			{:else}
			<div>
				<h2>{post.acf.article2.titre}</h2>
				<a href='{post.acf.article2.pdf}' target="_blank">PDF</a>
			</div>
			{/if}

		</div>

		</article>
	{/each}
