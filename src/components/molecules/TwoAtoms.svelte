<script>

    import Input from "../atoms/Input.svelte";
    import Button from "../atoms/Button.svelte";
    import { createEventDispatcher } from "svelte";

    let dispatch = createEventDispatcher();

    let btnText = 'Hello';
    let placeholder = 'Type your name...'
    let value = '';

</script>

    <p>This is an atom:</p>
    <Input bind:value={value} {placeholder}/>
    <p>This is also an atom:</p>
    <Button on:click={() => dispatch('setVisibleButtonPicker')} {btnText} bind:value={value}>, click me!</Button>

<style>

</style>