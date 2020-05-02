<script>
  let visible;
  function handleToggle() {
    visible = !visible;
  }
</script>

<footer>
  <div>
    <button on:click="{handleToggle}">
      +++Abonnement à <i>Plan Libre</i> 25€+++
    </button>
  </div>
  {#if visible}
  <div>
    <button on:click="{handleToggle}">×</button>
    <slot></slot>
    <div className="flex wrap jc-center">
      <a
        rel="noopener"
        target="_blank"
        href="https://www.paypal.com/webapps/hermes?token=5C288169KW5682405"
        className="btn"
      >
        Souscrire
      </a>
      <a
        rel="noopener"
        target="_blank"
        href="https://maop.fr/soutenir-la-maison"
        className="btn"
      >
        Soutenir la maison
      </a>
    </div>
  </div>
  {/if}
</footer>
