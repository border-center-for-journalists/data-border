<script>
	import Menu from './Menu.svelte';
	export let data; 
	const content = data.results[0].data;
	let showMenu = false;
	const openMenu = () => showMenu = true;
</script>
<nav class='main-nav'>
    <button class='menu-button' on:click={openMenu}></button>
    <a href='/' class='logo'> 
		<picture>
            <source media="(max-width: 700px)" srcset="img/logo_sm.png">
            <source media="(min-width: 701px)" srcset="img/logo_m.png">
    		<img alt='data border logo' src='img/logo_sm.png'> 
        </picture>
    </a>
    <nav class='social'>
        <a href='{content.facebook.url}' class='fb' target='_blank'> </a>
        <a href='{content.twitter.url}' class='tw' target='_blank'> </a>
        <a href='{content.youtube.url}' class='yt' target='_blank'> </a>
    </nav>
    <Menu menu='{content.menu}' bind:showMenu={showMenu}/>
</nav>