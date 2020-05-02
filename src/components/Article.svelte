<script>
  export let title, num, date, pdf;
  let visible;
  function handleToggle() {
    visible = !visible;
  }
</script>

<style>
  header {
    padding: 0.25em 1em;
    display: flex;
    justify-content: space-between;
    cursor: pointer;
  }
  .flex1 {
    flex: 1 1;
  }
  .flex2 {
    flex: 2 1;
  }
  .flex0 {
    flex: 0 1;
  }

  article {
    border-top: 1px solid black;
  }
</style>

<article>
  <header class="flex" on:click="{handleToggle}">
    <h2 class="flex1">{num}</h2>
    <h2 class="flex2">{title}</h2>
    <h2 class="flex2">{date}</h2>
    <h2 class="flex0">
      <a rel="noopener" target="_blank" href="{pdf}">PDF</a>
    </h2>
  </header>
  {#if visible}
  <slot></slot>
  {/if}
</article>
