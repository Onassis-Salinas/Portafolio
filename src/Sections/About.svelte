<script>
    import Icon from "../Components/Icon.svelte";
    import Section from "../Components/Section.svelte";
    let languageSelected;

    let images = ["Logos/HTML.svg", "Logos/CSS.svg", "Logos/JavaScript.svg", "Logos/React.svg", "Logos/Svelte.svg", "Logos/NodeJs.svg", "Logos/Expressjs.svg", "Logos/Python.svg", "Logos/django.svg", "Logos/Csharp.svg", "Logos/Net.svg", "Logos/VBA.svg", "Logos/MongoDB.svg", "Logos/MySQL.svg", "Logos/Firebase.svg", "Logos/Git.svg", "Logos/Github.svg", "Logos/VSCode.svg"];
</script>

<Section title={["Sobre mi", "About me"][languageSelected]} bind:languageSelected>
    <p>
        {[
            "Soy un programador apasionado por el desarrollo web y la automatización con más de 1 año de experiencia. Me encanta el diseño y crear soluciones innovadoras y atractivas que superen las expectativas de los clientes. Mis proyectos favoritos son aquellos cuya complejidad me pone a prueba.",
            "I'm a developer passionate about web development and automation with more than 1 year of experience. I love designing and creating innovative and attractive solutions that exceed client expectations. My favorite projects are those whose complexity tests me.",
        ][languageSelected]}
    </p>
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
