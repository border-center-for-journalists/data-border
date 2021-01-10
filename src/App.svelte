<script>
    import * as cms from 'cms.js';
    import Navigation from './components/Navigation.svelte';
    import AppDescription from './components/AppDescription.svelte';
    import SearchBox from './components/SearchBox.svelte';
    import Projects from './components/Projects.svelte';
    import Data from './components/Data.svelte';
    import Footer from './components/Footer.svelte';

    let currentPage;
    let searchText = '';

    $: getProjects = cms.getDocuments('proyecto');
    $: getData = cms.getDocuments('datum');   
    $: getCommon = cms.getDocuments('datoscomunes');

</script>

<main>
    
    {#await getCommon then data}
        <Navigation data={data} />
        <AppDescription data={data} />
    {/await}
    
    <SearchBox bind:searchText bind:currentPage />
    
    <div class='items'>
        {#await getProjects then projects}
            {#if currentPage === 'projects'}
                <Projects projects={projects.results} filter={searchText} />
            {/if}
        {/await}

        {#await getData then data}
            {#if currentPage === 'data'}
                <Data data={data.results} filter={searchText} />
            {/if}
        {/await}
    </div>

    <Footer />
</main>


<style>
.items {
    max-width: 840px;
    margin: 33px auto
}

</style>