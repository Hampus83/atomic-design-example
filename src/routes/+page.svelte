<script>
    import Input from "../components/atoms/Input.svelte";
    import ButtonPicker from "../components/molecules/ButtonPicker.svelte";
    import TwoAtoms from "../components/molecules/TwoAtoms.svelte";
    import SentenceGenerator from "../components/organisms/SentenceGenerator.svelte";
    import { word } from "../store";

    let visibleAtoms = true;
    let visibleButtonPicker = false;
    let visibleSentenceGenerator = false;

    let noOfBtns;
    let sentence = [];
    let result;
    
    let setWord;
    word.subscribe(value => setWord = value);

    const createSentence = () => {
        sentence.push(setWord);
        console.log(sentence);
        // result = sentence.map(word => {
        //     return word;
        // });
        // result.toString();
        result = sentence.join(' ');
        console.log(result);
    }

    const setVisibleButtonPicker = () => {
        visibleAtoms = false;
        visibleButtonPicker = true;
    }

    const setVisibleSentenceGenerator = () => {
        visibleButtonPicker = false;
        visibleSentenceGenerator = true;
    }

    // const test = () => {
    //     console.log(word);
    // }

</script>

    <main>
        <div class="wrapper">

            <h1>Atomic Design</h1>
            <img src="https://atomicdesign.bradfrost.com/images/content/atomic-design-process.png" alt="">

            {#if visibleAtoms}
                <TwoAtoms on:setVisibleButtonPicker={setVisibleButtonPicker} />  
            {:else if visibleButtonPicker}
                <ButtonPicker on:setVisibleSentenceGenerator={setVisibleSentenceGenerator} bind:noOfBtns={noOfBtns}/>
            {:else if visibleSentenceGenerator}
            <p class="p">This is an organism containing the same molecule(s) from before, plus the input-atom:</p>
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
    }

    * {
        box-sizing: border-box;
        margin: 0;
        text-align: center;
    }
    
    :global(p, h1) {
        font-family: 'Oswald', sans-serif;
    }

    main {
        background-color: #F4F3DB;
        padding-bottom: 3rem;
        /* width: 100vw; */
        min-height: 100vh;
    }

    .wrapper {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }

    h1 {
        text-transform: uppercase;
        margin-top: 2rem;
        /* position: absolute; */
        top: 1rem;
        font-size: 42px;
        font-weight: 500;
        letter-spacing: .2rem;
    }

    img {
        margin-top: 1rem;
        /* width: 50%; */
        width: 600px;
        height: 150px;
        object-fit: cover;
        margin-bottom: 1rem;
    }

    :global(p) {
        letter-spacing: .05rem;
        font-size: 20px;
        margin-bottom: 1rem;
        padding: 0 .5rem 0 .5rem;
    }

    .p {
        letter-spacing: .05rem;
        font-size: 20px;
        margin-bottom: 1rem;
        padding: 0 .5rem 0 .5rem;
        margin-top: 1.2rem;
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

    .input-wrapper :global(input) {
        font-size: 20px;
        padding: .5rem;
        text-align: center;
        border: 2px solid black;
        width: 100%;
        letter-spacing: .05rem;
    }

</style>
