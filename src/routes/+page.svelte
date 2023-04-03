<script>
    import Button from "../components/atoms/Button.svelte";
    import Input from "../components/atoms/Input.svelte";
    import ButtonPicker from "../components/molecules/ButtonPicker.svelte";
    import SentenceGenerator from "../components/organisms/SentenceGenerator.svelte";
    import { word } from "../store";
    import introImg from '../assets/intro.svg';
    import atomsImg from '../assets/atoms.svg';
    import moleculesImg from '../assets/molecules.svg';
    import organismsImg from '../assets/organisms.svg';
    import Image from "../components/atoms/Image.svelte";

    let visibleIntro = true;
    let visibleAtoms = false;
    let visibleButtonPicker = false;
    let visibleSentenceGenerator = false;

    let value = '';
    let noOfBtns;
    let sentence = [];
    let result;
    
    let setWord;
    word.subscribe(value => setWord = value);

    const createSentence = () => {
        sentence.push(setWord);
        result = sentence.join(' ');
    }

    const setVisibleAtoms = () => {
        visibleIntro = false;
        visibleAtoms = true;
    }

    const setVisibleButtonPicker = () => {
        visibleAtoms = false;
        visibleButtonPicker = true;
    }

    const setVisibleSentenceGenerator = () => {
        visibleButtonPicker = false;
        visibleSentenceGenerator = true;
    }

</script>

<main>

    <h1>Atomic Design</h1>
    <Image 
        src={visibleIntro ? introImg : visibleAtoms ? atomsImg : visibleButtonPicker ? moleculesImg : visibleSentenceGenerator ? organismsImg : null}
    />

    <div class="wrapper">

        {#if visibleIntro}
            <br>
            <h2>A quick demonstration</h2>
            <div class="btn-wrapper">
                <Button btnClass on:click={setVisibleAtoms} btnText="Let's go!" value=''/>
            </div>

        {:else if visibleAtoms}
            <p>This is an atom:</p>
            <Input bind:value={value} placeholder='Type your name...'/>
            <p>This is also an atom:</p>
            <Button btnClass on:click={setVisibleButtonPicker} btnText='Hello' bind:value={value}>, click me!</Button> 

        {:else if visibleButtonPicker}
            <p class="first">This is a molecule consisting of the two prior atoms:</p>
            <p class="but">(but, with some other characteristics...)</p>
            <ButtonPicker on:setVisibleSentenceGenerator={setVisibleSentenceGenerator} bind:noOfBtns={noOfBtns}/>
            <p class="enter">enter a number between 1 and 5</p>

        {:else if visibleSentenceGenerator}
            <p class="p">This is an organism containing the same molecule(s) from before, as well as the input-atom:</p>
            <div class="sentence-wrapper">
                {#each Array(parseInt(noOfBtns)) as component}
                    <SentenceGenerator on:createSentence={createSentence}/>
                {/each}
            </div>
            <div class="input-wrapper">
                <Input placeholder='Create a sentence with the inputs...' bind:value={result} />
            </div>
        {/if}

    </div>

</main>

<style>

    @import url('https://fonts.googleapis.com/css2?family=Oswald:wght@200;300;400;500;600;700&display=swap');

    :global(body) {
        margin: 0;
        width: 100vw;
        min-height: 100vh;
        background-color: #F5F4DC;
    }

    * {
        box-sizing: border-box;
        margin: 0;
        text-align: center;
    }
    
    :global(p, h1, h2) {
        font-family: 'Oswald', sans-serif;
    }

    main {
        padding-bottom: 3rem;
        max-width: 100%;
        max-height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .wrapper {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        
    }

    h1 {
        padding-top: 10rem;
        text-transform: uppercase;
        font-size: 42px;
        font-weight: 500;
        letter-spacing: .2rem;
    }

    :global(p) {
        letter-spacing: .05rem;
        font-size: 20px;
        margin-bottom: 1rem;
        padding: 0 .5rem 0 .5rem;
    }

    p {
        letter-spacing: .05rem;
        font-size: 20px;
        margin-bottom: 1rem;
        padding: 0 .5rem 0 .5rem;
        margin-top: 1.2rem;
    }

    h2 {
        margin-top: 2rem;
        letter-spacing: .2rem;
        font-weight: 400;
    }

    .sentence-wrapper {
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
        padding: 0 4rem;
        gap: 2rem;
        margin-bottom: 2rem;
    }

    .input-wrapper {
        width: 80%;
    }

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

    .input-wrapper :global(input) {
        font-size: 20px;
        padding: .5rem;
        text-align: center;
        border: 2px solid black;
        width: 100%;
        letter-spacing: .05rem;
    }

    .btn-wrapper :global(button) {
        margin-top: 5rem;
    }

</style>
