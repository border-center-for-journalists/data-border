<script>
    import * as cms from 'cms.js';
    import GithubCircle from "svelte-material-icons/GithubCircle.svelte";
    import LinkVariant from "svelte-material-icons/LinkVariant.svelte";

    export let project;

    const icons = {
        github : GithubCircle,
        link : LinkVariant
    }

</script>
<article>
    <header>
        <nav>
            <img src='img/app-icon.png' alt='app-icon' />
            <span>{project.type}</span>
        </nav>
        <h2>{project.title[0].text}</h2>
    </header>
    {@html cms.formatHTML(project.description)}
    <ul class='project-links'>
        {#each project.links as link}
            <li>
                <a href='{link.link.url}' target='{link.link.target}' >
                    <span class='icon'><svelte:component this={icons[link.icon]}/></span>
                    {link['link-title'][0].text}
                </a>
            </li>
        {/each}
    </ul>
    <div class='bg-img'>
        <picture>
            <source media="(max-width: 700px)" srcset="{project.image.Small.url}">
            <source media="(min-width: 701px)" srcset="{project.image.url}">
            <img src="{project.image.url}" alt="{project.image.alt}">
        </picture>
    </div>
    <div class='bg-color'></div>
</article>
<style>

    article {
        color: white;
        padding: 10px 25px;
        position: relative;
    }
    article header {
        height: 170px;
        margin-bottom: 35px;
    }
    article .bg-color {
        position: absolute;
        top: 0;
        left: 0;
        display:block;
        width: 100%;
        height: 100%;
        background: black;
        z-index: -2;
    }
    article .bg-img {
        position: absolute;
        top: 0;
        left: 0;
        z-index: -1;
        display: block;
        max-height: 180px;
        overflow: hidden;
        max-width:100%;
    }

    article .bg-img::after {
        content: "";
        display: block;
        width: 100%;
        height: 100%;
        position: absolute;
        top: 0;
        left: 0;
        background-image: linear-gradient(to top, rgba(0,0,0,0), rgba(0,0,0,.88) 65%);
    }

    article h2 {
        font-size: 2.2em;
        font-weight: bold;
        margin: 0;
        letter-spacing: 0.03em;
    }

    @media(min-width: 700px) {
        article {
            padding: 10px 55px;
        }

        article h2 {
            font-size: 3em;
            letter-spacing: 0.05em;
        }
        article .bg-img{
            max-height: 250px;
        }
        article header{
            height:240px;
        }
    }

    article nav {
        color: #f3e536;
        font-weight: bold;
        font-size: .95em;
        border-bottom: 2px solid #f3e536;
        letter-spacing: 2.4px;
        margin-bottom: 5px;
        justify-content: flex-end;
        line-height: 31px;
        padding: 8px 0 15px 0;
        z-index: 1;
        text-transform: uppercase;
    }

    article nav img {
        margin-right: 10px;
    }
    article {
        margin: 25px 0 50px;
    }
    .project-links{
        list-style-type: none;
        padding:0;
    }
    .project-links a{
        color:white;
        display: flex;
    }
    .project-links a:hover span{
        background-color: white;
        color:black;
        transition: all 0.5s ease 0s;
    }
    .project-links li{
        line-height: 46px;
        margin:15px 5px 0;
    }
    .project-links .icon{
        font-size:30px;
        margin-right:15px;
        padding:6px 15px 0;
        border: 1px solid white;
        line-height: 30px;
    }
</style>