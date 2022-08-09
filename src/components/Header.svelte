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
    box-shadow: 0 0 0.5rem var(--orange);
    transition: box-shadow 0.4s;
  }

  header:hover {
    box-shadow: 0 0 1.5rem var(--orange);
  }

  a {
    width: 100%;
    height: 100%;
    cursor: pointer;
  }

  img {
    height: 15.3px;
    position: absolute;
    left: 50%;
    transform: translate(-50%);
    top: 3rem;
  }
</style>
