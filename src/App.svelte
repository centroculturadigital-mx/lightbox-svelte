<script>

    import LightBox from "./LightBox.svelte"

    let images = Array(10).fill(1).map(()=>({
		url: "http://unsplash.it/300/"+parseInt((Math.random()*200)+200),
		title: "Minim in sunt aliquip adipisicing excepteur non."
	}))

</script>


<ul class="Imagenes">

    {#each images as image,i ("imagen_"+i)}
		<img src={image.url} alt={image.title}/>
    {/each}

</ul>


<LightBox content={images}/>