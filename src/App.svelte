<script>

    import LightBox from "./LightBox.svelte"
	let w;
	let h;

	const words=[
		"ritual",
		"mountain",
		"desert",
		"world",
		"music",
		"textile",
		"water",
		"wind",
		"cloud",
	]

	w = 300;
	h = 200;
    let images = Array(10).fill(1).map((e,i)=>({
		url: `https://fakeimg.pl/${w}x${h}?text=Image-${i}`,
		title: "Minim in sunt aliquip adipisicing excepteur non."
	}))
	
	w = 800;
	h = 600;
    let imagesFull = Array(10).fill(1).map((e,i)=>({
		url: `https://fakeimg.pl/${w}x${h}?text=Image-${i}`,
		title: "Minim in sunt aliquip adipisicing excepteur non."
	}))

</script>


<ul class="Imagenes">

    {#each images as image,i ("imagen_"+i)}
		<img src={image.url} alt={image.title}/>
    {/each}

</ul>


<LightBox content={imagesFull}/>