<script>
	import Menu from "./Menu.svelte"
	import AddMenuItem from "./AddMenuItem.svelte"
	
	
	let menu = [{title: 'Home',content :'Content to be shown when "home" is selected'},
							{title: 'About',content :'Content to be shown when "about" is selected'},
							{title: 'Contact',content :'Content to be shown when "contact" is selected'}
							];
	let selected = 'Home';
	let showForm = false;
	
	function handleSelectedMenuItemChange(event) {
		 selected = event.detail.title;
	}
	
	function handleAddButtonClicked(event) {
	   showForm = true;
	}
	
	function handleSubmitItem(event){
	const newMenuItem = event.detail;
	for (const item of menu) { 
    if (newMenuItem.title === item.title){
    alert('menu item already exist!');
		showForm = false;
		return;
		}
	} 
  menu = menu.concat({ title: newMenuItem.title, content: newMenuItem.content });
  alert("New menu item " + newMenuItem.title + " is added successfully ! ")
	showForm = false;	    
	} 
</script>

<Menu {selected} {menu}  on:selectedMenuItemChange={handleSelectedMenuItemChange} on:onAddButtonClicked={handleAddButtonClicked} />

 <main>
	  {#each menu as menuItem}
	   {#if selected == menuItem.title}
   <div>
		 {menuItem.content}
	 </div>
    {/if}
	{/each}
		{#if showForm}
	     <AddMenuItem {menu} on:submitItem={handleSubmitItem}/>
    {/if}
</main>


<style>
	main {
		max-width: 500px;
		margin: 40px auto;
		padding: 15px;
		border: 2px solid;
	}
	
	main > div {
		border: 1px solid;
		margin: 10px 0;
		padding: 30px;
	}
</style>
