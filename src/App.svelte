<script>
    import * as cms from 'cms.js';
    import Navigation from './components/Navigation.svelte';
    import AppDescription from './components/AppDescription.svelte';
    import Project from './components/Project.svelte';
    import Footer from './components/Footer.svelte';
    
    $: getProjects = cms.getDocuments('proyecto');   
    $: getCommon = cms.getDocuments('datoscomunes');
</script>

<main>
    {#await getCommon then data}
    <Navigation data={data} />
    <AppDescription data={data} />
    {/await}

    {#await getProjects then projects}
    <section class='projects'>
        {#each projects.results as project}
            <Project project={project.data}/>
        {/each}
    </section>
    {/await}
    <Footer />
</main>

