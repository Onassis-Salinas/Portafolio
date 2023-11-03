<script>
    import { slide } from "svelte/transition";
    import { language } from "../store.js";

    let languageSelected = 0;

    const unsubscribe = language.subscribe((value) => (languageSelected = value));

    function changeLanguage(value) {
        language.set(value);
    }

    let scroll = 0;
    window.addEventListener("scroll", () => {
        scroll = window.scrollY;
    });

    let show = false;
    setTimeout(() => {
        show = true;
    }, 2500);
</script>

{#if show}
    <div class="container" transition:slide>
        <p on:click={() => changeLanguage(1)} class="left">English</p>
        <p on:click={() => changeLanguage(0)} class="rigth">Español</p>
    </div>
{/if}

<style>
    div {
        position: absolute;
        top: 30px;
        display: flex;
        gap: min(50vw, 500px);
    }
    .left {
        transform: rotateZ(-5deg);
    }
    .rigth {
        transform: rotateZ(5deg);
    }
</style>
