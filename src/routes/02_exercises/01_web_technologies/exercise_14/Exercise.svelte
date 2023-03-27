<script>
  let current = "";
</script>

<!-- We will cover buttons later on! -->
<button class="btn btn-secondary" on:click={() => (current = "messi")} class:selection={current==="messi"}>
  Messi
</button>

<button class="btn btn-secondary" on:click={() => (current = "ronaldo")} class:selection={current==="ronaldo"}>
  Ronaldo
</button>

<button class="btn btn-secondary" on:click={() => (current = "neymar")} class:selection={current==="neymar"}>
  Neymar
</button>


<style>
  .selection{background-color: blueviolet;}
</style>