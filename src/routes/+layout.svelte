<script>
  import "../app.css";
  let { children } = $props();

  import { onMount } from "svelte";
  import { autoModeWatcher } from "@skeletonlabs/skeleton";

  onMount(() => {
    autoModeWatcher();
  });
</script>

{@render children()}
