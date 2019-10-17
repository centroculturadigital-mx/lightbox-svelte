<script>

	import LightBox from "./LightBox.svelte"

	let nextContent=0

	const openLightBox = (i) => {
		nextContent = i
	}

	let w = 300;
	let h = 200;

	let images = Array(3).fill(1).map((e,i)=>({
		small: `https://fakeimg.pl/${w}x${h}?text=Image-${i}`,
		full: `https://fakeimg.pl/${w*2}x${h*2}?text=Image-${i}`,
		title: "Minim in sunt aliquip adipisicing excepteur non."
	}))

</script>


<ul class="Imagenes">

    {#each images as image,i ("imagen_"+i)}
		<img
			src={image.small}
			alt={image.title}
			on:click={()=>openLightBox(i)}
		/>
    {/each}

</ul>


<LightBox content={images} go={nextContent}/>