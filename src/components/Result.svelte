<script>
    export let result = {
        name:'',
        email:''
    };

    $:console.log({result});
</script>

<div class="nes-container with-title is-centered">
    <p class="title">Resultado:</p>
    <p class="nes-balloon from-left nes-pointer">
        Nombre: {result.profile.name || ""}.
    </p>
    <p class="nes-balloon from-right nes-pointer">
        Email: {result.profile.email || ""}.
    </p>
    {#if result.details.description}
        <p class="nes-balloon from-left nes-pointer">
            Descripción: {result.details.description}
        </p>
    {:else}
        <p class="nes-balloon from-left nes-pointer">
            La descripción es opcional.
        </p>
    {/if}
</div>