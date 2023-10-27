<script>
    import Icon from "../Components/Icon.svelte";
    import Section from "../Components/Section.svelte";
    let languageSelected;

    let images = ["Logos/HTML.svg", "Logos/CSS.svg", "Logos/JavaScript.svg", "Logos/React.svg", "Logos/Svelte.svg", "Logos/NodeJs.svg", "Logos/Expressjs.svg", "Logos/Python.svg", "Logos/django.svg", "Logos/Csharp.svg", "Logos/Net.svg", "Logos/VBA.svg", "Logos/MongoDB.svg", "Logos/MySQL.svg", "Logos/Firebase.svg", "Logos/Git.svg", "Logos/Github.svg", "Logos/VSCode.svg"];
</script>

<Section title={["Sobre mi", "About me"][languageSelected]} bind:languageSelected>
    <p>{["Soy un programador enfocado en el desarrollo web y la automatizacion de tareas, me gusta usar las ultimas tecnologias y modas de diseño para mis proyectos para siempre generar los mejores resultados.", "dasdasd"][languageSelected]}</p>
    <h3>{["Tecnologias", "Technologies"][languageSelected]}</h3>
    <div id="technologies-container">
        {#each images as image}
            <Icon route={image} />
        {/each}
    </div>
</Section>

<style>
    #technologies-container {
        display: flex;
        gap: 10px;
        flex-wrap: wrap;
        justify-content: center;
    }
</style>
