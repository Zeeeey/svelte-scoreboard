<script>
  import { createEventDispatcher } from "svelte";

  export let name;
  export let points;
  let showControls = false;

  const dispatch = createEventDispatcher();

  const addPoint = () => (points += 1);
  const removePoint = () => (points -= 1);
  const toggleControls = () => (showControls = !showControls);
  const deletePlayer = () => dispatch("deleteplayer", name);
</script>

<div class="card">
  <h1>
    {name}
    <button class="btn btn-sm" on:click={toggleControls}>
      {#if showControls} -{:else}+{/if}
    </button>
    <button class="btn btn-sm btn-danger" on:click={deletePlayer}>
      Delete
    </button>
  </h1>
  <h3>Points: {points}</h3>
  {#if showControls}
    <button class="btn" on:click={addPoint}>+1</button>
    <button class="btn btn-dark" on:click={removePoint}>-1</button>
    <input type="number" bind:value={points} />
  {/if}
</div>

<style>
  h1 {
    color: #204f6e;
  }
  h3 {
    margin-bottom: 10px;
  }
</style>
