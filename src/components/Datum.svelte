<script>
	import * as cms from 'cms.js';
    import ProgressDownload from "svelte-material-icons/ProgressDownload.svelte";
    import FileDelimited from "svelte-material-icons/FileDelimited.svelte";
    import Xml from "svelte-material-icons/Xml.svelte";
    import PdfBox from "svelte-material-icons/PdfBox.svelte";
    import GoogleSpreadsheet from "svelte-material-icons/GoogleSpreadsheet.svelte";
    import ZipBox from "svelte-material-icons/ZipBox.svelte";
    import Database from "svelte-material-icons/Database.svelte";

	export let datum;

	const icons = {
        csv : FileDelimited,
        xml : Xml,
        pdf : PdfBox,
        xlsx : GoogleSpreadsheet,
        zip : ZipBox,
        mysql : Database,
    }
	
	let isOpen = false;
</script>

<article>
	<div class='summary'>
	    <div>
		    <h2>{datum.title[0].text}</h2>
		    <div class='description'>{@html cms.formatHTML(datum.description)}</div>
		    <p class='source'><b>Fuente:</b> {datum.source}</p>
		    <p class='formats'>
			    {#each datum.formats as format}
			    	<span class='format'>
			    		<i><svelte:component this={icons[format.format]}/></i>
			    		{format.format}
			    	</span>
			    {/each}
			</p>
		</div>
		<a href='{datum.link.url}' target='{datum.link.target}' class='download-btn'>
			<span class='icon'><ProgressDownload /></span>
			<span>Descargar</span>
		</a>
		<button class='expand-btn' class:open={isOpen} on:click={() => isOpen = !isOpen}>+</button>
	</div>
	<div class='metadata' class:open={isOpen}>
		<h3>Meta Datos</h3>
		<table>
			{#each datum.metadata as row }
			<tr>
				<td><b>{row.label}</b></td>
				<td>{row.value}</td>
			</tr>
			{/each}
		</table>
	</div>
</article>

<style>
	.description a{
		color: black;
	}
	article{
		background-color: #F0F0F0;
		padding: 20px 40px;
		font-size:15px;
		margin-bottom:25px;
	}
	.summary{
		display:flex;
		flex-direction: column;
		align-items: center;
	}
	@media(min-width: 825px) {
		.summary{
			flex-direction: row;
		}
	}

	.summary div{
		flex-grow: 1;
	}
	.summary p{
		margin: 5px 0;
	}
	.summary h2{
		font-size:19px;
		font-weight: normal;
		margin: 0 0 10px 0;
	}
	.summary .source{
		font-style: italic;
	}
	.summary .format{
		display:block;
		background-color: #C1C1C1;
		color:white;
		font-size:13px;
		margin:0 5px 5px 0 ;
		width: 80px;
		text-align:center;
		line-height: 36px;


	}
	.summary .format i{
		font-size:17px;
		position:relative;
		top:4px;
	}
	.summary .formats{
		display: flex;
		margin-top:10px;
		flex-wrap: wrap;
	}
	.metadata{ 
		max-height: 0px;
		overflow: hidden;
    	transition: max-height .15s ease;
	}
	.metadata.open{
		max-height:3000px;		
    	transition: max-height 0.15s ease;
	}
	.metadata h3{
		width:100%;
		border-bottom: 1px solid black;
		text-transform: uppercase;
		font-size:14px;
		margin-bottom: 0px;
	}
	.metadata table{
		width: 100%;		
  		border-collapse: collapse;
	}
	.metadata table tr{
		border-bottom: 1px solid #E4E4E4;
		line-height: 28px;
		font-size:13px;
	}
	
	.download-btn{
		display: block;
		background-color:black;
		color: #F5E538;
		line-height:38px;
		height:38px;
		text-decoration: none;
		font-size:14px;
		text-transform: uppercase;
		padding:10px 20px 10px 10px;
		display: flex;
		margin-top: 15px;
    	transition: background-color,color .25s ease;
	}

	.download-btn:hover{
		background-color: #F5E538;
		color:black;
	}
	.download-btn .icon{
		font-size:35px;
		margin-right:7px;
	}

	.expand-btn{
		border: 2px solid black;
		color: black;
		font-size:33px;
		border-radius:50%;
		line-height: 33px;
		min-width:36px;
		padding: 0;
		margin:20px 0 0 25px;
    	transition: background-color .25s ease;
	}

	.expand-btn.open{
		color: #F0F0F0;
		background-color: black;
    	transition: background-color .25s ease;
	}

</style>