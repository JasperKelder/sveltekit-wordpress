<script context="module">
  import { BASE_URL, POSTS_API_URL } from '$lib/variables';

  export const load = async request => {
    const slug = request.params.slug;
    const res = await fetch(`${BASE_URL}${POSTS_API_URL}?slug=${slug}&_embed`);
    const posts = await res.json();
    const post = posts[0];
    post.image = post._embedded['wp:featuredmedia'][0].source_url;
    post.author = post._embedded.author[0].name;

    return {
      props: {
        post,
      },
    };
  };
</script>

<script>
  export let post;
</script>

<h1>{@html post.title.rendered}</h1>
<p><small>{new Date(post.date)}</small></p>
<p><b>by {post.author}</b></p>
{#if post.image}
  <img src={post.image} alt={post.title.rendered} />
{/if}
<p>{@html post.content.rendered}</p>
