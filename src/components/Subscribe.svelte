<script>
  let visible;
  function handleToggle() {
    visible = !visible;
  }
</script>

<footer>
  <div class="bc marquee fixed b0 r0 z200">
    <button class="p0111" on:click="{handleToggle}">
      +++Abonnement à <i>Plan Libre</i> 25€+++
    </button>
  {#if visible}
  <div class="p">
    <div class="flex jc-sb">
      <span></span>
      <h3>title</h3>
      <button on:click="{handleToggle}">×</button>
    </div>
    <slot></slot>
    <div class="flex wrap jc-center">
      <a
        rel="noopener"
        target="_blank"
        href="https://www.paypal.com/webapps/hermes?token=5C288169KW5682405"
        class="btn"
      >
        Souscrire
      </a>
      <a
        rel="noopener"
        target="_blank"
        href="https://maop.fr/soutenir-la-maison"
        class="btn"
      >
        Soutenir la maison
      </a>
    </div>
  </div>
  {/if}
</footer>
