<script>
    import * as cms from 'cms.js';
    import GithubCircle from "svelte-material-icons/GithubCircle.svelte";
    import LinkVariant from "svelte-material-icons/LinkVariant.svelte";

    export let project;
    console.log(project);

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
    }
    .project-links li{
        line-height: 62px;
        margin:10px 5px;
    }
    .project-links .icon{
        font-size:30px;
        margin-right:5px;
        padding:10px 15px 3px;
        border: 1px solid white;
    }
</style>