<script>

    import Carousel from "@centroculturadigital-mx/svelte-carousel";

    export let content;
    export let go;

    let classBase = "LightBox"
    
    let classList = `${classBase} ${classBase}--hidden`

    $: contents = Array.isArray(content) ? content : [content]

    $: open(go)

    const open = (goIndex) => {
        if( !! goIndex ) {
            classList = classBase
        }
    }

    const close = () => {
        classList = `${classBase} ${classBase}--hidden`
    }
 
</script>


<style>




    .LightBox {
        position: fixed;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
    }
    .LightBox header {
        width: 100%;
        position: absolute;
        top: 0;
        left: 0;
        z-index: 1;
        display: flex;
        align-items: center;
        justify-content: flex-end;
    }
    
    .LightBox :global(.carousel)
    /* ,
    .LightBox :global(.slides)  */
    {
        width: 100vw;
        height: 100vh;
    }
    .LightBox :global(.slides > * > *) {

        /* width: 100vw !important;
        height: 70vh !important; */
        height: 100vh;
        display: flex;
        align-items: center;
        justify-content: center;

    }
    .LightBox :global(.carousel > ul) {
        bottom: 0;
    }

    .LightBox :global(.carousel img) {
        object-fit: contain;
    }

    .Lightbox__Overlay {
        position: absolute;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: rgba(0,0,0,0.7);
        opacity: 1;
        transition: opacity 1s;
    }

    .LightBox--hidden {
        display: none;
        opacity: 0;
    }
    


</style>



<div class={classList}>
    <header>
        <button on:click={close}>
            Close
        </button>
    </header>
    
    <div class="Lightbox__Overlay"></div>
    <Carousel perPage={({perParge:1})} go={go}>
            
        {#each contents as content,i ("content_"+i)}
            {#if content.type=="image"|| !content.type }
                <img src={content.full} alt={content.title}>
            {/if}
        {/each}

    </Carousel>
    

</div>