<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

{@render children?.()}

<style lang="scss">
  @import "../styles/pico.scss";

  :global(body) {
    max-width: 600px;
    margin: 0 auto;
    padding: 2rem;
  }
</style>

