<script>
    import Button from "../atoms/Button.svelte";
    import Input from "../atoms/Input.svelte";
    import { createEventDispatcher } from "svelte";

    let dispatch = createEventDispatcher();

    // let btnText = 'OK';
    let placeholder = '';
    export let noOfBtns = '';

    const addNoOfBtns = () => { 
        console.log(noOfBtns);
        if (noOfBtns >= 1 && noOfBtns <= 5) {
            dispatch('setVisibleSentenceGenerator')
        } else {
            alert('nope!');
        }
    }

    const updateNoOfBtns = (event) => {
        noOfBtns = event.target.value;
        console.log(noOfBtns);
    }

    console.log(noOfBtns);

</script>

    <p class="first">This is a molecule consisting of the two prior atoms:</p>
    <p class="but">(but, with some other characteristics...)</p>
    <div class="wrapper">
        <Input on:input={updateNoOfBtns} {placeholder} bind:value={noOfBtns}/>
        <Button on:click={addNoOfBtns} value='' btnText=''>
            <i class="fa-solid fa-thumbs-up"></i>
        </Button>
        </div>
        <p class="enter">enter a number between 1 and 5</p>

<style>

    .wrapper {
        display: flex;
        justify-content: center;
        /* align-items: center; */
        gap: .5rem;
    }

    /* .input-wrapper {
        display: flex;
        flex-direction: column;
    } */

    .first {
        margin-bottom: .5rem;
    }

    .but {
        margin-top: 0;
        color: #C16100;
        font-size: 18px;
    }

    .enter {
        margin: 0;
        margin-left: -5.5rem;
        font-size: 16px;
    }

</style>