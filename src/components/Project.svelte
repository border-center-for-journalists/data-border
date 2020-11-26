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
    .project-links{
        list-style-type: none;
        padding:0;
    }
    .project-links a{
        color:white;
        text-decoration: none;
        display: flex;
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