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

<h1>SvelteKit Wordpress</h1>
{#each posts as post}
  <h2>{@html post.title.rendered}</h2>
  <img src={post.image} alt={post.title.rendered} />
  <p>{@html post.excerpt.rendered}</p>
  <a sveltekit:prefetch href={`/posts/${post.slug}`}>Read More</a>
{/each}
