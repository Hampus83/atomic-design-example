<script>
    import Button from "../atoms/Button.svelte";
    import Input from "../atoms/Input.svelte";
    import {word} from '../../store';
    import { createEventDispatcher } from "svelte";

    let dispatch = createEventDispatcher();

    export let btnText = 'Add';

    let checked = false;
    let checkedClass = 'checkedClass';
    
    const handleClick = () => {
        dispatch('createSentence');
        checked = true;
    }

    const updateWord = (event) => {
        word.set(event.target.value);
    }

</script>

    <div class="wrapper">
        <Input on:input={updateWord} value='' placeholder='Type a word...'/>
        <Button on:click={handleClick} value='' btnClass={checked ? checkedClass : ''} btnText={checked ? '' : btnText}>
            {#if checked}
                <i class="fa-solid fa-check"></i>
            {/if}
        </Button>
    </div>

<style>

    .wrapper {
        display: flex;
        gap: .5rem;
    }

    .wrapper :global(button) {
        width: 5rem;
    }

</style>