<script>
	let clicked = false;
	
	

</script>

<div>
	<button class="btn btn-primary" on:click={() => (clicked = true)}>
		{#if !clicked}
			<p>You have to click te button!</p>
		{:else}
			<p>Buttom clicked</p>
		{/if}
	</button>	
</div>
