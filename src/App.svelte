<script>
  import { onMount } from "svelte";

  export let name;

  let profile;

  onMount(async () => {
    const res = await fetch("/api/profile");
    const json = await res.json();
    profile = json;
  });
</script>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<main>
  <h1>Hello {name}!</h1>
  {#if profile}
    <code>{JSON.stringify(profile)}</code>
  {:else}
    <code>loading ...</code>
  {/if}
</main>
