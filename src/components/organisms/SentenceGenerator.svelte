<script>
    import Button from "../atoms/Button.svelte";
    import Input from "../atoms/Input.svelte";
    import {word} from '../../store';
    import { createEventDispatcher } from "svelte";

    let dispatch = createEventDispatcher();

    export let btnText = 'Add';
    
    const handleClick = () => {
        console.log(word);
        dispatch('createSentence');
    }

    const updateWord = (event) => {
        word.set(event.target.value);
    }

</script>

    <div class="wrapper">
        <Input on:input={updateWord} value='' placeholder='Type a word...'/>
        <Button on:click={handleClick} value='' {btnText}/>
    </div>

<style>

    .wrapper {
        display: flex;
        gap: .5rem;
    }

</style>