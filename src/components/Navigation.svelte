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

<style>
    
nav {
    display: flex;
}

nav .menu-button {
    border: none;
    width: 50px;
    height: 50px;
    background: black url(../img/hamburger-menu.png) center center no-repeat;
    background-size: 20px
}

nav .logo {
    line-height: 0;
}

nav .logo img {
    height: 50px;
    object-fit: contain;
}

nav.social {
    margin-left: auto;
    padding: 0 12px;
    background: white;
    display: none;
}

@media(min-width: 700px) {
    nav .logo img {
        height: 75px;
    }

    nav .menu-button {
        width: 75px;
        height: 75px;
        background-size: auto;
    }

    nav.social {
        display: flex;
    }
}

nav.social a {
    background-color: #fff200;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    margin: auto 8px;
    background-position: center center;
    background-repeat: no-repeat;
}

nav.social a.fb {
    background-image: url(../img/fb-C.png);
}

nav.social a.tw {
    background-image: url(../img/tw-C.png);
}

nav.social a.yt {
    background-image: url(../img/yt-C.png);
}
</style>