<script>
    import TranslationMenu from './TranslationMenu.svelte'
    import MaterialIcon from './MaterialIcon.svelte'

    let innerWidth
    let opened = localStorage.getItem('header') === null ? true : JSON.parse(localStorage.getItem('header'));

    function toggleOpen(){
        //toggle and save to local storage
        opened = !opened
        localStorage.setItem('header', opened)
    }

</script>

<svelte:window bind:innerWidth={innerWidth}/>

<header>
    {#if innerWidth > 768}
        <div class="header-bar">
            <h3 class="title is-3" id="title">Who's Open CB6</h3>
            <div class="buttons has-text-right">
                <TranslationMenu className="is-small"/>
                <button class="button is-small {opened ? 'is-clicked' : ''}" on:click={toggleOpen}>
                    <MaterialIcon icon="info"></MaterialIcon>
                </button>
            </div>
        </div>
        {#if opened}
            <div id="subtitle">
                <p class="is-6 subtitle"><strong>Directory of Bussiness in Manhattan Community District 6</strong>
                    <br/><br/>We are updating these listings regularly, but please check their Instagram, website, or
                    call for the most current information.</p>
                <div class="buttons are-small">
                    <a href="https://airtable.com/shrsHyRioPufGGSpz" target="_blank" class="button is-info">Missing Business or Outdated Info?</a>
                    <a href="mailto:zhi@beta.nyc" target="_blank" class="button is-info">Submit Feedback</a>
                </div>
            </div>
        {/if}
    {:else}
        <div class="header-bar">
            <h3 class="title is-5">Who's Open CB6</h3>
            <div class="buttons has-text-right">
                <TranslationMenu className="is-small"/>
                <button class="button is-small {opened ? 'is-clicked' : ''}" on:click={toggleOpen}>
                    <MaterialIcon icon="info"></MaterialIcon>
                </button>
            </div>
        </div>
        {#if opened}
            <div id="subtitle">
                <p class="is-6 subtitle"><strong>Directory of Bussiness in Manhattan Community District 6</strong>
                    <br/><br/>We are updating these listings regularly, but please check their Instagram, website, or
                    call for the most current information.</p>
                <div class="buttons are-small">
                    <a href="https://airtable.com/shrsHyRioPufGGSpz" target="_blank" class="button is-info">Missing Business or Outdated Info?</a>
                    <a href="mailto:zhi@beta.nyc" target="_blank" class="button is-info">Submit Feedback</a>
                </div>
            </div>
        {/if}
    {/if}
</header>

<style>
    .header-bar {
        margin: 1rem 0rem;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        justify-content: space-between;
    }

    .title {
        margin-bottom: 10px !important;
    }

    .has-background-warning {
        padding: 0.2rem 1rem;
    }

    @media only screen and (max-width: 768px) {

        #subtitle {
            margin-top: 5px;
            background-color: #eaeaea;
            padding: 1rem 2rem;
            z-index: 2;
        }
    }

    .is-clicked {
        background-color: #ecf1f8;
    }

    p {
        margin-bottom: 0.25rem !important;
    }
</style>