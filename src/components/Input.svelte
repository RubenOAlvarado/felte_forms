<script>
    export let name = "";
    export let id = "";
    export let label = "";
    export let placeholder = "Some...";
</script>

<div class="nes-field">
    <label for={id}>{label}</label>
    <input
        class="nes-input"
        type="text"
        {id}
        {name}
        {placeholder}
        aria-describedby={`${name}-validation`}
    />
    <div id={`${name}-validation`} data-felte-reporter-dom-for={name} class="nes-text is-error" aria-live="polite" />
</div>