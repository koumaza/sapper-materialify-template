<script>
  import { MaterialApp } from "svelte-materialify/src";
  import Nav from "../components/Nav.svelte";

  export let segment;
</script>

<style global>
  a {
    text-decoration: none;
  }
</style>

<MaterialApp>
  <Nav {segment} />
  <slot />
</MaterialApp>
