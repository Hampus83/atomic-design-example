<script>

    export let btnText;
    export let value;

</script>

    <button on:click >{btnText} {value}<slot></slot></button>

<style>

    button {
        border: none;
        font-family: 'Oswald', sans-serif;
        font-size: 24px;
        background-color: #DC7F28;
        border: 3px solid black;
        /* min-width: 10rem; */
        padding: .5rem 1.5rem;
        cursor: pointer;
    }

    button:hover {
        /* opacity: .7; */
        background-color: #bf7c3d;
    }

</style>