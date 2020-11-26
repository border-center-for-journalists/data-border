<script>
    import * as cms from 'cms.js';
	export let data;
	const content = data.results[0].data;
</script>

<section class='intro'>
    <content>
        <!-- TODO figure out why this much cleaner code doesnt work
        	<h1>{@html cms.formatHTML(content.titulo_general)}</h1> -->
        <h1>{content.titulo_general[0].text}</h1>
        <hr/>
        {@html cms.formatHTML(content.description)}
    </content>
</section>

<style>
h1{
    font-size: 29px;
    text-align: center; 
    margin-bottom: 15px;
}

.intro{
    text-align: center;
    color: white;
    background: black;
    padding: 20px 0;
}

.intro content{
    max-width:740px;
    margin: 0 auto;
    display: block;
    padding: 0 20px;
}

.intro hr{
   border-color: #F3E536;
   width:150px;
}

@media(min-width: 700px){
    h1{
        font-size:36px;
    }
    .intro content{
        padding: 0 55px;
    }
}
</style>