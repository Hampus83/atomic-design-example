<script>
    

</script>

<main>
    <h1>LIA2: Nykundsuppdrag - Bönor & Blad</h1>

    <div class="wrapper">
        <ol>
            <li>
                <a target="_blank" href="https://bonorochblad.se/">Research befintlig site</a>
            </li>
            <li>
                <a target="_blank" href="https://docs.google.com/document/d/1d3T8etdKdfF6BYnMwBeauIivvqRbl5YqCb_zyW9y-dA/edit">Uppstartsmöte med kund</a>
            </li>
            <li>
                <a target="_blank" href="https://www.figma.com/file/5lgdfpo0HowilBTSan6pNF/B%C3%B6nor-%26-Blad?type=design&node-id=0%3A1&t=PdONyLfqzwVvdw3l-1">Figmaskiss</a>
            </li>
            <li>
                <a target="_blank" href="https://docs.google.com/document/d/1TilUDRAq_Rek8SDMnyG3Ug06d3Mt_buTNvsb31FvVgU/edit">Kundmöte: Genomgång av figmaskiss och synpunkter</a>
            </li>
            <li>
                <a target="_blank" href="https://www.figma.com/file/5lgdfpo0HowilBTSan6pNF/B%C3%B6nor-%26-Blad?type=design&node-id=0%3A1&t=PdONyLfqzwVvdw3l-1">Korrigeringar och tillägg i figmaskiss</a>
            </li>
        </ol>
        <ol>
            <li>
                <a target="_blank" href="https://test9.cdsuperstore.se/sv/">Utveckling</a>
            </li>
            <li>
                <a target="_blank" href="https://test9.cdsuperstore.se/sv/">Kundtest</a>
            </li>
            <li>
                <a target="_blank" href="https://test9.cdsuperstore.se/sv/">Korrigering</a>
            </li>
            <li>
                <a target="_blank" href="https://test9.cdsuperstore.se/sv/">Lansering</a>
            </li>
        </ol>
    </div>

    <a href="https://test9.cdsuperstore.se/webbadmin?funk=edit_front_page&id=1">webbadmin</a>
</main>

<style>

    @import url('https://fonts.googleapis.com/css2?family=Oswald:wght@200;300;400;500;600;700&display=swap');

    :global(body) {
        margin: 0;
        max-width: 100vw;
        min-height: 100vh;
        background-color: #003A43;
        color: #FF585D;
    }

    * {
        box-sizing: border-box;
        margin: 0;
        text-align: center;
        line-height: 150%;
        letter-spacing: 0.1em;
    }
    
    :global(p, li, h1, h2) {
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

    h1 {
        margin-top: 5rem;
        border-bottom: 2px solid #b3b3b3;
        width: 80%;
        padding-bottom: 1rem;
        text-transform: uppercase;
        margin-bottom: 3rem;
    }

    .wrapper {
        display: flex;
        
    }

    ol {
        margin-bottom: 3rem;
        list-style: none;
        /* counter-reset: counter; */
        padding-left: 0;
        /* columns: 2; */
    }

    ol:first-of-type {
        counter-reset: mycounter;
    }

    li {
        text-align: left;
        padding: 1rem;
        font-size: 20px;
        position: relative;
        margin-bottom: 2rem;
        font-weight: 300;
    }

    li::before {
        counter-increment: mycounter;
        content: counter(mycounter);
        color: #b3b3b3;
        font-weight: 900;
        font-style: italic;
        font-size: 14px;
        position: absolute;
        top: -1.7%;
        left: 1.2rem;
    }

    li a {
        padding: .5rem 1rem;
        border: 2px solid transparent;
    }

    li a:hover {
        border-color: #FF585D;
        transition: .15s ease-in-out;
    }

    a {
        text-decoration: none;
        color: inherit;
    }

</style>
