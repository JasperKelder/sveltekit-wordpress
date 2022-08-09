<script context="module">
  import { BASE_URL, POSTS_API_URL } from '$lib/variables';

  export const load = async () => {
    const res = await fetch(`${BASE_URL}${POSTS_API_URL}?_embed`);
    const posts = await res.json();
    posts.map(post => {
      post.image = post._embedded['wp:featuredmedia'][0].source_url;
    });

    return {
      props: {
        posts,
      },
    };
  };
</script>

<script>
  export let posts;
</script>

<ul>
  {#each posts as post}
    <li class="post">
      <a sveltekit:prefetch href={`/posts/${post.slug}`}>
        <h2>{@html post.title.rendered}</h2>
        <img src={post.image} alt={post.title.rendered} width="1000px" />
        <p>{@html post.excerpt.rendered}</p>
      </a>
    </li>
  {/each}
</ul>

<style>
  ul {
    list-style-type: none;
  }

  .post {
    position: relative;
    text-align: center;
    padding-bottom: 50px;
    cursor: pointer;
  }

  .post h2,
  .post p {
    position: absolute;
    left: 50%;
    transform: translate(-50%, -50%);
    color: var(--orange);
    text-shadow: 0 0 1rem var(--black);
    transition: text-shadow 0.6s;
  }

  .post h2 {
    top: 25%;
    font-size: 4rem;
  }

  .post p {
    bottom: 25%;
    font-size: 1.8rem;
    color: var(--white);
  }

  img {
    box-shadow: 0 0 1rem var(--black);
    transition: box-shadow 1s;
  }

  img:hover {
    box-shadow: 0 0 2rem var(--orange);
  }
</style>
