<script>
    import { language } from "../store.js";

    let languageSelected = false;
    let languageValue;

    const unsubscribe = language.subscribe((value) => (languageValue = value));

    function changeLanguage(value) {
        language.set(value ? 1 : 0);
    }

    $: changeLanguage(languageSelected);
</script>

<header>
    <input type="checkbox" name="" id="" bind:checked={languageSelected} />
    <p>{languageSelected ? "English" : "Español"}</p>
</header>

<style>
    header {
        display: flex;
        height: 50px;
        position: fixed;
        z-index: 999;
        background-color: var(--fc);
    }
</style>
