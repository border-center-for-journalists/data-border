<script>
    import * as cms from 'cms.js';
    import Project from './components/Project.svelte';
    import Navigation from './components/Navigation.svelte';
    
    $: getProjects = cms.getDocuments('proyecto');   
    //$: getCommon = cms.getDocuments('commonData');
</script>

<main>
	<Navigation />
    <section class='projects'>
        {#await getProjects then projects}
            {#each projects.results as project}
                <Project project={project.data}/>
            {/each}
        {/await}
    </section>
</main>

<style>

</style>