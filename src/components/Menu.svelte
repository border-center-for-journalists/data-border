<script>	
    import Close from "svelte-material-icons/Close.svelte";
    export let menu; 
    export let showMenu;

    const closeMenu = () => showMenu = false;
</script>

<div class='overlay' on:click={closeMenu} class:show='{showMenu}' ></div>
<div class='side-menu' class:show='{showMenu}'>
	<img alt='data border logo' src='img/logo_sm.png'> 
	<button class='close-button' on:click={closeMenu}><Close/></button>
	<menu>
		{#each menu as item}
			<li>
				<a  href='{item.link.url}' target='{item.link.target}'>{item.link_title[0].text}</a>
			</li>
		{/each}
	</menu>
</div>

<style>
menu {
	padding-left:0;
}

menu li{
	list-style-type: none;
	padding:15px 0;
}

menu li a{
	text-decoration: none;
	color: black;
	font-weight: bold;

}

.side-menu{
	transition: opacity 0.5s ease 0s;
	background: white;
	width:100%;
	position: absolute;
	padding: 20px 27px;
	color: black;
	font-size:18px;
	box-sizing: border-box;
	z-index: 5;
	visibility:hidden;
	opacity: 0;
}

.close-button{
	width:65px;
	height: 65px;
	float:right;
	font-size: 55px;
	margin-top:-5px;
	line-height: 41px;
}

.overlay{
	transition: opacity 0.5s ease 0s;
	position: fixed;
	opacity: 0;
	background: #333;
	width:100%;
	height:100%;
	z-index: 4;
	visibility:hidden;
}

.overlay.show{
	visibility: visible;
	opacity: .5;
}

.side-menu.show{
	visibility: visible;
	opacity: 1;
}


@media(min-width: 700px){
	.side-menu{
		max-width: 500px;
	}
}
</style>