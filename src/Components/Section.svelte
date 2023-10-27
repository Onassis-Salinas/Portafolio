<script>
    import { language } from "../store";
    export let languageSelected;
    const unsubscribe = language.subscribe((val) => (languageSelected = val));
    export let title;
</script>

<section>
    <h2>{title}</h2>
    <slot />
</section>
