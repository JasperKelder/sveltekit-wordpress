<script context="module">
  export const load = async ({ url: { pathname } }) => ({
    props: { pathname },
  });
</script>

<script>
  import Header from '../components/Header.svelte';
  import PageTransition from '../components/PageTransition.svelte';

  export let pathname;
</script>

<Header />
<PageTransition {pathname}>
  <div class="wrapper">
    <slot />
  </div>
</PageTransition>

<style>
  :root {
    --white: #ffffff;
    --black: #000000;
    --orange: #ff6600;
    --purple: #190336;
  }

  :global(*, *::after, *::before) {
    margin: 0;
    padding: 0;
    box-sizing: inherit;
  }

  :global(html) {
    scroll-behavior: smooth;
    font-size: 62.5%;
  }

  :global(body) {
    font-size: 1.6rem;
    box-sizing: border-box;
    scrollbar-gutter: stable;
    font-family: sans-serif;
  }

  :global(img) {
    max-width: 100%;
    border-radius: 1.5%;
  }

  :global(.more-link) {
    display: none;
  }

  .wrapper {
    width: 80vw;
    margin: 85px auto;
    padding-top: 30px;
    text-align: center;
  }
</style>
