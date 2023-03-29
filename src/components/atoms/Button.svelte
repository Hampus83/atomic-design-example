<script>

    export let btnText;
    export let value;
    export let btnClass;

</script>

    <button class={btnClass} on:click >{btnText} {value}<slot></slot></button>

<style>

    button {
        border: none;
        font-family: 'Oswald', sans-serif;
        font-size: 24px;
        background-color: #DC7F28;
        border: 3px solid black;
        padding: .5rem 1.5rem;
        cursor: pointer;
    }

    button:hover {
        background-color: #bf7c3d;
    }

    .checkedClass {
        background-color: rgb(20, 85, 20);
        pointer-events: none;
    }

    .checkedClass:hover {
        background-color: rgb(20, 85, 20);
        pointer-events: none;
    }

</style>