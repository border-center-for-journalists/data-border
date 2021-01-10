<script>
    import Datum from '../components/Datum.svelte';

	export let data;
	export let filter; 

	$: filteredData = data.filter(d => {
		return [
			d.data.title[0].text,
			d.data.description[0].text,
			d.data.source
		]
		.join(' ')
		.toLowerCase()
		.indexOf(filter.toLowerCase()) !== -1;
	})
	.sort((a,b) => a.data.title[0].text.toLowerCase() < b.data.title[0].text.toLowerCase() ? -1 : 1);
	
</script>
{#each filteredData as datum}
	<Datum datum={datum.data} />
{/each}