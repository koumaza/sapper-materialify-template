<script>
  import { AppBar, Button } from "svelte-materialify/src";

  export let segment;
</script>

<AppBar>
  <a slot="title" href="/" class="text--primary"> Home </a>
  <div style="flex-grow:1" />
    <a href="/about/">
      <Button text active={segment === 'about'}>About</Button>
    </a>
    <a href="/blog/">
      <Button text active={segment === 'blog'}>Blog</Button>
    </a>
</AppBar>
