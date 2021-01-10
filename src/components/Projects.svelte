<script>
    import Project from '../components/Project.svelte';
	export let projects;
	export let filter;

	$: filteredProjects = projects
		.filter(p => {
			const searchDomain = p.data.title[0].text.toLowerCase() + ' ' + p.data.description[0].text.toLowerCase();
			return searchDomain.indexOf(filter.toLowerCase()) !== -1;
		})
		.sort((a,b) => a.data.title[0].text.toLowerCase() < b.data.title[0].text.toLowerCase() ? -1 : 1);
</script>

{#each filteredProjects as project}
    <Project project={project.data}/>
{/each}
