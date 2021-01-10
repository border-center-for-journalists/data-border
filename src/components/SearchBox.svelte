<script>
    import Magnify from "svelte-material-icons/Magnify.svelte";
	
	export let searchText = '';
	export let currentPage = 'projects';
</script>
<nav>
	<button class:selected={currentPage === 'projects'} on:click='{() => currentPage = 'projects'}' > Proyectos </button>
	<button class:selected={currentPage === 'data'} on:click='{() => currentPage = 'data'}' > Datos </button>
	<form>
		<span ><Magnify /></span>
		<input type='text' placeholder="buscar" bind:value={searchText}/>
	</form>
</nav>
<style>
	nav{
		max-width: 840px;
		margin:0 auto;
		display: flex;
	}
	nav > button{
		background-color: #F0F0F0;
		color: #717171;
		text-transform: capitalize;
		font-size:19px;
		padding:15px 0;
		width:190px;
		line-height: 30px;
    	transition: background-color .25s ease;
	}
	button.selected{
		background-color: black;
		color:white;		
    	transition: background-color .25s ease;
	}
	form{
		height:62px;
		background-color: #F5E538;
		color:black;
		flex-grow: 1;
		display: flex;
	}
	form input{
		border: none;
		border-bottom: 2px solid black;
		border-radius: 0;
		background-color: transparent;
		flex-grow: 1;
		margin:17px 55px 17px 0;
	}
	form input:focus{
		outline: none;
	}
	form span{
		font-size: 34px;
		line-height:72px;
		padding:0 12px;
	}
</style>