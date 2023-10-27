<script>
    import { scale, fade } from "svelte/transition";

    import { language } from "../store";
    import Icon from "./Icon.svelte";
    let languageSelected;
    const unsubscribe = language.subscribe((val) => (languageSelected = val));

    export let showProject;
    export let title;
    export let assets;
    export let technologies;
    export let projectLinks;

    let scrollDiv;

    $: if (!showProject) {
        setTimeout(() => {
            scrollDiv.scrollTop = 0;
        }, 300);
    }
</script>

{#if showProject}
    <div class="shadow container" in:fade out:fade={{ delay: 300 }} on:click={() => (showProject = false)} />
    <div class="container" in:scale={{ delay: 300 }} out:scale bind:this={scrollDiv}>
        <img src="/x.svg" alt="" class="close-button" on:click={() => (showProject = false)} />
        <h2>{title[languageSelected]}</h2>

        {#each assets as asset}
            {#if asset.includes(".jpg") || asset.includes(".png") || asset.includes(".webp")}
                <img src={asset} alt="" />
            {:else}
                <p>{asset[languageSelected]}</p>
            {/if}
        {/each}

        <h3>{["Tecnologias usadas:", "Used technologies:"][languageSelected]}</h3>
        <div class="technologies-container">
            {#each technologies as tech}
                <Icon route={tech} />
            {/each}

            <div class="links-container">
                {#each projectLinks as link}
                    {#if link.includes("github")}
                        <a href={link}><button class="github"><img src="Logos/Github.svg" alt="" />{"Github"}</button></a>
                    {:else}
                        <a href={link}><button class="link"><img src="/link.svg" alt="" />{["Visitar", "Visit"][languageSelected]}</button></a>
                    {/if}
                {/each}
            </div>
        </div>
    </div>
{/if}

<style>
    .container {
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: calc(min(90%, 600px) - 40px);
        height: 90lvh;
        overflow-y: auto;
        display: flex;
        flex-direction: column;
        padding: 20px;
        background-color: var(--fc);
        border-radius: var(--br);
    }
    h2 {
        margin-top: 0;
    }
    p {
        margin-top: 10px;
        margin-bottom: 50px;
    }
    img {
        border-radius: var(--br);
    }
    .close-button {
        position: fixed;
        top: 20px;
        right: 20px;
        width: 30px;
        aspect-ratio: 1/1;
    }
    a {
        padding: 0px;
    }
    .links-container {
        width: 100%;
        display: flex;
        flex-wrap: wrap;
        gap: 10px;
        justify-content: center;
        margin-top: 30px;
    }
    button {
        padding: 5px 20px;
        height: 50px;
        border: none;
        cursor: pointer;
        border-radius: var(--br);
        font-size: var(--fs3);
        display: flex;
        gap: 5px;
        align-items: center;
        transition: all .2s ease;
    }
    button:hover{
        transform: translateY(-5px);

    }
    button img{
        height: 100%;
        aspect-ratio: 1;
    }
    .github {
        background-color: #24292d;
        color: #fff;
    }
    .link {
        color: #000;
        background-color: #fff;
    }
    .shadow {
        width: 110vw;
        height: 110vh;
        background-color: rgba(0, 0, 0, 0.7);
    }
    .technologies-container {
        display: flex;
        justify-content: center;
        gap: 10px;
        flex-wrap: wrap;
    }
</style>
