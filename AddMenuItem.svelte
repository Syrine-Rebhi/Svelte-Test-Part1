<script>
	import { createEventDispatcher } from 'svelte';
  let dispatch = createEventDispatcher();
	let menuItemTitle = '';
	let menuItemContent = '';	
	
  function handleAddNewMenuItem () {
	  const formValues = {title: menuItemTitle,content: menuItemContent};
		dispatch('submitItem',formValues);
	}

</script>

<div>
	<input type="text" placeholder="Add new menu item" bind:value={menuItemTitle}>	
	<textarea placeholder="text to show when we click on the new item" bind:value={menuItemContent}></textarea>
	<button on:click={handleAddNewMenuItem}>
		Add menu item
	</button>
</div>

<style>
	input, textarea {
		margin-top: 15px;
		padding: 10px;
		border: 1px solid #777;
		width: 100%;
	}
</style>
