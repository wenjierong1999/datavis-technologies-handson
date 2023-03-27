<script>
	let clicked = false;
</script>

<div>
	<button class="btn btn-primary" on:click={() => (clicked = true)}>
		click here
	</button>
	<!--  -->
	{#if clicked == true}
	<span>You have clicked the button!</span>
	{:else}
	<span>You have to click the button!</span>
	{/if}
</div>
