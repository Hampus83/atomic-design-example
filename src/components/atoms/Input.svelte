<script>

    export let placeholder;
    export let value;

</script>

    <input on:input min="1" max="5" bind:value={value} type='text' placeholder={placeholder}>

<style>

    input {
        font-size: 20px;
        padding: .5rem;
        text-align: center;
        border: 2px solid black;
        letter-spacing: .05rem;
        outline: none;
    }

</style>