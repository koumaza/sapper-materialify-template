<script context="module">
  export async function preload({ params, query }) {
    // the `slug` parameter is available because
    // this file is called [slug].svelte
    const res = await this.fetch(`blog/${params.slug}.json`);
    const data = await res.json();

    if (res.status === 200) {
      return { post: data };
    } else {
      this.error(res.status, data.message);
    }
  }
</script>

<script>
  import { Container } from "svelte-materialify/src";
  export let post;
</script>

<svelte:head>
  <title>{post.title}</title>
</svelte:head>

<Container class="content">
  <h1 class="text-h3 mb-4 mt-3">{post.title}</h1>
  {@html post.html}
</Container>
