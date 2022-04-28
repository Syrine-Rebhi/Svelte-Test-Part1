<script>
	export let menu;
	export let selected ;
	import AddMenuItem from "./AddMenuItem.svelte"
	
	import { createEventDispatcher } from 'svelte';
  let dispatch = createEventDispatcher();
	
</script>

<div class="menu">
	{#each menu as item}
		<div class="menu-item" class:selected={selected == item.title} on:click={() => dispatch('selectedMenuItemChange', item)}>
			{item.title}
		</div>
	{/each}
	
	<button on:click={() => dispatch('onAddButtonClicked')}>
		Add New Menu Item
	</button>
</div>

<style>
	.menu {
		margin-top: 30px;
		display: flex;
		width: 100%;
		justify-content: center;
		align-items: center;
	}
	
	.menu .menu-item {
		padding: 10px 6px;
		margin: 0 5px;
		font-size: 16px;
		cursor: pointer;
	}
	
	.menu .menu-item.selected {
		border-bottom: 4px solid #000;
	}
</style>
