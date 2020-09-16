<script context="module">
  export function preload({ params, query }) {
    return this.fetch(`blog.json`)
      .then((r) => r.json())
      .then((posts) => {
        return { posts };
      });
  }
</script>

<script>
  import { Container, List, ListItem } from "svelte-materialify/src";
  export let posts;
</script>

<svelte:head>
  <title>Blog</title>
</svelte:head>

<Container>
  <h1 class="mt-2 mb-3">Recent posts</h1>
  <List>
    {#each posts as post}
      <!-- we're using the non-standard `rel=prefetch` attribute to
		   tell Sapper to load the data for the page as soon as
		   the user hovers over the link or taps it, instead of
		   waiting for the 'click' event -->
      <a rel="prefetch" href="blog/{post.slug}">
        <ListItem>{post.title}</ListItem>
      </a>
    {/each}
  </List>
</Container>
