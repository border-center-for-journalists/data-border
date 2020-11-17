<script>
    import * as cms from 'cms.js';
    import Project from './components/Project.svelte';
    import Navigation from './components/Navigation.svelte';
    
    $: getProjects = cms.getDocuments('proyecto');   
    //$: getCommon = cms.getDocuments('commonData');
</script>

<main>
	<Navigation />
    <section class='intro'>
        <h1>Data Border es la plataforma de datos de BorderHub</h1>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras varius sodales posuere. Vestibulum eu faucibus dui. Suspendisse quis orci in sapien venenatis feugiat. Vivamus vehicula dolor sit amet porttitor convallis.</p>
        <p>Integer commodo tincidunt metus. Nullam faucibus pharetra leo, nec pulvinar arcu hendrerit et. Fusce nisi dui, ornare sit amet feugiat ac, fermentum vel mauris.</p>
    </section>
    <section class='projects'>
        {#await getProjects then projects}
            {#each projects.results as project}
                <Project project={project.data}/>
            {/each}
        {/await}
    </section>
</main>

<style>
h1{
    font-size: 50px;
    text-align: center; 
}
.intro{
    max-width:1020px;
    padding:0 20px;
    margin: 0 auto;
    text-align: justify;
}
</style>