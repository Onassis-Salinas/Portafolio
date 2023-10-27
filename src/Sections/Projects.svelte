<script>
    import Project from "../Components/Project.svelte";
    import Section from "../Components/Section.svelte";
    let languageSelected;
    let showProject = false;
    let projectData;
    let projectTitle;
    let projectTechnologies;

    const projectSections = [
        {
            title: ["Paginas web", "Landing Pages"],
            projects: [
                { title: ["Pagina de cafeteria", "Coffe shop website"], image: "/Images/page7.png", index: 0 },
                { title: ["Portafolio fotografico impactante", "Impactfull photographer portfolio"], image: "/Images/page1.png", index: 1 },
                { title: ["Ecommerce simple", "Simple ecommerce"], image: "/Images/page11.png", index: 2 },
                { title: ["Portafolio fotografico elegante", "Elegant photographer portfolio"], image: "/Images/page3.png", index: 3 },
                { title: ["Pagina de cafeteria moderna", "Modern coffe shop website"], image: "/Images/page9.png", index: 4 },
                { title: ["Portafolio fotografico simple", "Simple photographer portfolio"], image: "/Images/page5.png", index: 5 },
            ],
            image: "",
        },
        {
            title: ["Aplicaciones web", "Web applications"],
            projects: [{ title: ["Sistema de gestion RH", "RH gestion system"], image: "", index: 0 }],
            image: "",
        },
        {
            title: ["Automatizacion", "Automatization"],
            projects: [
                { title: ["Impresora de etiquetas", "Ticket Printer"], image: "", index: 0 },
                { title: ["Impresora de credenciales", "Credentials Printer"], image: "", index: 0 },
            ],
        },
        {
            title: ["Programas en excel", "Excel Applications"],
            projects: [{ title: ["Sistema de captura de datos", "Data capture system"], image: "", index: 0 }],
        },
    ];

    function selectProject(title, index) {
        showProject = true;
        projectData = projectsData[index];
        projectTitle = title;
        projectTechnologies = projectsTechnologies[index];
    }

    const projectsData = [
        ["/Images/page7.png", ["Una landing page profesional que sigue los estándares de diseño.", "A professional landing page following design standards."], "/Images/page8.png", ["Diseño responsive para todo tipo de pantallas y un estilo llamativo.", "Responsive design for all types of screens and an eye-catching style."], "https://cafeteria-od1.netlify.app/"],
        ["/Images/page1.png", ["Un portafolio con diseño simple e impactante listo para mostrar las mejores fotos.", "A portfolio with a simple and impressive design ready to showcase the best photos."], "/Images/page2.png", ["Fotografías que destacan entre tanta simplicidad, generando un espacio cautivador.", "Photographs that stand out amidst such simplicity, creating a captivating space."], "https://photographer-portfolio-od3.netlify.app/"],
        ["/Images/page11.png", ["Tienda en línea con artículos de ciclismo.", "E-commerce with bike articles."], "/Images/page12.png", ["Diseño moderno y responsive que cumple con todas las necesidades de un negocio.", "Modern and responsive design that meets all business requirements."], "https://ecommerce-3a4dd.web.app/"],
        ["/Images/page3.png", ["Un portafolio elegante que resalta la belleza de las fotografías exhibidas.", "An elegant portfolio that highlights the beauty of the displayed photographs."], "/Images/page4.png", ["Una galería que abarca toda la pantalla, creando una experiencia única.", "A gallery that covers the entire screen, creating a unique experience."], "https://photographer-portfolio-od2.netlify.app/"],
        ["/Images/page9.png", ["Diseño moderno y refrescante a la altura de una gran cafetería.", "Modern and refreshing design befitting a great coffee shop."], "/Images/page10.png", ["Un estilo minimalista sin perder el toque distintivo.", "A minimalist style without losing its distinctive touch."], "https://cafeteria-od2.netlify.app/"],
        ["/Images/page5.png", ["Una barra lateral y una galería, más que suficiente cuando se acompañan de excelentes fotografías.", "A sidebar and a gallery, more than enough when accompanied by excellent photographs."], "/Images/page6.png", ["Diseño responsive listo para cualquier dispositivo, conservando la esencia del diseño.", "Responsive design ready for any device while preserving the essence of the design."], "https://photographer-portfolio-od1.netlify.app/"],
    ];

    const projectsTechnologies = [
        ["Logos/HTML.svg", "Logos/CSS.svg", "Logos/JavaScript.svg", "Logos/Svelte.svg"],
        ["Logos/HTML.svg", "Logos/CSS.svg", "Logos/JavaScript.svg", "Logos/Svelte.svg"],
        ["Logos/HTML.svg", "Logos/CSS.svg", "Logos/JavaScript.svg", "Logos/Svelte.svg"],
        ["Logos/HTML.svg", "Logos/CSS.svg", "Logos/JavaScript.svg", "Logos/Svelte.svg"],
        ["Logos/HTML.svg", "Logos/CSS.svg", "Logos/JavaScript.svg", "Logos/Svelte.svg"],
        ["Logos/HTML.svg", "Logos/CSS.svg", "Logos/JavaScript.svg", "Logos/Svelte.svg"],
    ];
</script>

<Section title={["Proyectos", "Projects"][languageSelected]} bind:languageSelected>
    {#each projectSections as projectSection}
        <h3>{projectSection.title[languageSelected]}</h3>
        <div class="projects-container">
            {#each projectSection.projects as project}
                <div class="project" on:click={() => selectProject(project.title, project.index)}>
                    <img src={project.image} alt="" />
                    <p>{project.title[languageSelected]}</p>
                </div>
            {/each}
        </div>
    {/each}
</Section>

<Project title={projectTitle} assets={projectData} technologies={projectTechnologies} bind:showProject />

<style>
    .projects-container {
        display: flex;
        gap: 10px;
        flex-shrink: 0;
        overflow-x: auto;
        align-items: flex-start;
    }
    .project {
        align-self: flex-start;
        flex-shrink: 0;
        width: 300px;
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 10px;
        background-color: var(--fc);
        border-radius: var(--br);
    }
    p {
        margin: 0;
        margin-top: 5px;
    }

    img {
        width: 90%;
        aspect-ratio: 16/9;
        object-fit: cover;
    }
</style>
