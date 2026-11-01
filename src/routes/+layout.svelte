<script>
  import favicon from "#lib/assets/favicon.svg";
  import "./global_stylesheet.css";
  import Navbar from "#lib/assets/components/nav.svelte";
  let { children } = $props();
</script>

<svelte:head>
  <link rel="icon" href={favicon} />
</svelte:head>

<Navbar></Navbar>

{@render children()}
