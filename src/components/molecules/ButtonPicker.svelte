<script>
    import Button from "../atoms/Button.svelte";
    import Input from "../atoms/Input.svelte";
    import { createEventDispatcher } from "svelte";

    let dispatch = createEventDispatcher();

    let placeholder = '';
    export let noOfBtns = '';

    const addNoOfBtns = () => { 
        if (noOfBtns >= 1 && noOfBtns <= 5) {
            dispatch('setVisibleSentenceGenerator')
        } else {
            alert('nope!');
        }
    }

    const updateNoOfBtns = (event) => {
        noOfBtns = event.target.value;
    }

</script>

    <div class="wrapper">
        <Input on:input={updateNoOfBtns} {placeholder} bind:value={noOfBtns}/>
        <Button btnClass on:click={addNoOfBtns} value='' btnText=''>
            <i class="fa-solid fa-thumbs-up"></i>
        </Button>
    </div>


<style>

    .wrapper {
        display: flex;
        justify-content: center;
        gap: .5rem;
    }

</style>