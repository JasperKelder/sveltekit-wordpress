<script>
  import { page } from '$app/stores';
</script>

<header>
  <a sveltekit:prefetch href="/" class:active={$page.url.pathname === '/'}>
    <img
      id="logo"
      width="208.659"
      height="15.297"
      src="logo.png"
      alt="Fundament All Media"
    />
  </a>
</header>

<style>
  header {
    height: 85px;
    top: 0;
    display: flex;
    align-items: center;
    vertical-align: center;
    position: fixed;
    width: 100vw;
    z-index: 2;
    background-color: var(--white);
    border-bottom: 0.2rem solid var(--orange);
  }

  img {
    height: 15.3px;
    margin-left: 25px;
  }
</style>
