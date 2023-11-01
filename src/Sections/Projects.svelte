<script>
    import Project from "../Components/Project.svelte";
    import ProjectsContainer from "../Components/ProjectsContainer.svelte";
    import Section from "../Components/Section.svelte";
    let languageSelected = 0;
    let showProject;
    let projectData;
    let projectTitle;
    let projectLinks;
    let projectTechnologies;

    function selectProject(title, index) {
        showProject = true;
        projectData = projectsData[index];
        projectTitle = title;
        projectTechnologies = projectsTechnologies[index];
        projectLinks = projectsLinks[index];
    }

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
        // {
        //     title: ["Aplicaciones web", "Web applications"],
        //     projects: [{ title: ["Sistema de gestion RH", "RH gestion system"], image: "", index: 0 }],
        //     image: "",
        // },
        {
            title: ["Automatizacion", "Automation"],
            projects: [
                { title: ["Impresora de etiquetas", "Ticket Printer"], image: "/Images/auto1.jpg", index: 6 },
                { title: ["Impresora de credenciales", "Credentials Printer"], image: "/Images/auto8.jpg", index: 7 },
            ],
        },
        // {
        //     title: ["Programas en excel", "Excel Applications"],
        //     projects: [{ title: ["Sistema de captura de datos", "Data capture system"], image: "", index: 0 }],
        // },
    ];

    const projectsData = [
        ["/Images/page7.png", ["Una landing page profesional que sigue los estándares de diseño.", "A professional landing page following design standards."], "/Images/page8.png", ["Diseño responsive para todo tipo de pantallas y un estilo llamativo.", "Responsive design for all types of screens and an eye-catching style."]],
        ["/Images/page1.png", ["Un portafolio con diseño simple e impactante listo para mostrar las mejores fotos.", "A portfolio with a simple and impressive design ready to showcase the best photos."], "/Images/page2.png", ["Fotografías que destacan entre tanta simplicidad, generando un espacio cautivador.", "Photographs that stand out amidst such simplicity, creating a captivating space."]],
        ["/Images/page11.png", ["Tienda en línea con artículos de ciclismo.", "E-commerce with bike articles."], "/Images/page12.png", ["Diseño moderno y responsive que cumple con todas las necesidades de un negocio.", "Modern and responsive design that meets all business requirements."]],
        ["/Images/page3.png", ["Un portafolio elegante que resalta la belleza de las fotografías exhibidas.", "An elegant portfolio that highlights the beauty of the displayed photographs."], "/Images/page4.png", ["Una galería que abarca toda la pantalla, creando una experiencia única.", "A gallery that covers the entire screen, creating a unique experience."]],
        ["/Images/page9.png", ["Diseño moderno y refrescante a la altura de una gran cafetería.", "Modern and refreshing design befitting a great coffee shop."], "/Images/page10.png", ["Un estilo minimalista sin perder el toque distintivo.", "A minimalist style without losing its distinctive touch."]],
        ["/Images/page5.png", ["Una barra lateral y una galería, más que suficiente cuando se acompañan de excelentes fotografías.", "A sidebar and a gallery, more than enough when accompanied by excellent photographs."], "/Images/page6.png", ["Diseño responsive listo para cualquier dispositivo, conservando la esencia del diseño.", "Responsive design ready for any device while preserving the essence of the design."]],
        [
            "/Images/auto5.jpg",
            [
                "Problema: Se necesitan crear etiquetas en base a la información de órdenes en PDF, esto toma de 5-30 minutos dependiendo de la orden, esto es propenso a fallo si se copia mal la información, además la medición manual dificulta generar un formato exacto.",
                "Problem: Labels need to be created based on order information in PDFs. This takes 5-30 minutes depending on the order, and it is error-prone if the information is copied incorrectly. Additionally, manual measurement makes it difficult to generate an exact format.",
            ],
            "/Images/auto6.jpg",
            ["Este es uno de los PDFs de los que se extrae la información, se copian los datos necesarios y se pegan en la etiqueta.", "This is one of the PDFs from which the information is extracted. The necessary data is copied and pasted onto the label."],
            "/Images/auto1.jpg",
            "/Images/auto3.jpg",
            ["Se generó un programa que al ingresar el código de la orden, se te genera un menú con: las etiquetas necesarias (cada tipo de orden lleva etiquetas diferentes), la cantidad de cada una y la cantidad de producto por caja.", "A program was created that, upon entering the order code, generates a menu with the necessary labels (each type of order requires different labels), the quantity of each one, and the product quantity per box."],
            "/Images/auto2.jpg",
            ["Gracias al programa, el proceso de generar etiquetas pasó de 5-30 minutos a menos de 1 minuto, los errores prácticamente se eliminaron y se generó un formato exacto para más profesionalidad.", "Thanks to the program, the process of generating labels went from 5-30 minutes to less than 1 minute. Errors were virtually eliminated, and an exact format was created for added professionalism."],
        ],
        [
            "/Images/auto8.jpg",
            ["Un programa simple para generar credenciales desde una base de datos con los datos de empleados y su foto, solo agregando su identificador (en este caso, número de empleado) se generan las dos caras de su credencial.", "A simple program to generate credentials from a database with employee data and their photo. Just by adding their identifier (in this case, employee number), both sides of their credential are generated."],
            "/Images/auto7.jpg",
            ["En cuestión de segundos regresa dos imágenes con todos los datos en el formato dado. Esto ayuda a que todas las credenciales sean exactamente iguales para mantener cierta profesionalidad además de facilitar su creación a solo unos clics.", "In a matter of seconds, it returns two images with all the data in the specified format. This ensures that all credentials are exactly the same to maintain a certain level of professionalism and makes their creation as easy as a few clicks."],
        ],
    ];

    const projectsTechnologies = [
        ["Logos/HTML.svg", "Logos/CSS.svg", "Logos/JavaScript.svg", "Logos/Svelte.svg"],
        ["Logos/HTML.svg", "Logos/CSS.svg", "Logos/JavaScript.svg", "Logos/Svelte.svg"],
        ["Logos/HTML.svg", "Logos/CSS.svg", "Logos/JavaScript.svg", "Logos/Svelte.svg", "Logos/Firebase.svg"],
        ["Logos/HTML.svg", "Logos/CSS.svg", "Logos/JavaScript.svg", "Logos/Svelte.svg"],
        ["Logos/HTML.svg", "Logos/CSS.svg", "Logos/JavaScript.svg", "Logos/Svelte.svg"],
        ["Logos/HTML.svg", "Logos/CSS.svg", "Logos/JavaScript.svg", "Logos/Svelte.svg"],
        ["Logos/Python.svg"],
        ["Logos/Python.svg"],
    ];

    const projectsLinks = [
        ["https://cafeteria-od1.netlify.app/", "https://github.com/Onassis-Salinas/Cafeteria-Practice1"],
        ["https://photographer-portfolio-od3.netlify.app/", "https://github.com/Onassis-Salinas/photographer3"],
        ["https://ecommerce-3a4dd.web.app/"],
        ["https://photographer-portfolio-od2.netlify.app/", "https://github.com/Onassis-Salinas/Photographer2"],
        ["https://cafeteria-od2.netlify.app/", "https://github.com/Onassis-Salinas/Cafeteria-3"],
        ["https://photographer-portfolio-od1.netlify.app/", "https://github.com/Onassis-Salinas/Photographer"],
        ["https://github.com/Onassis-Salinas/Ticket-Printer"],
        ["https://github.com/Onassis-Salinas/Impresora-de-credenciales"],
    ];
</script>

<Section title={["Proyectos", "Projects"][languageSelected]} bind:languageSelected>
    {#each projectSections as projectSection}
        <ProjectsContainer {projectSection} bind:languageSelected {selectProject} />
    {/each}
</Section>
<Project title={projectTitle} assets={projectData} technologies={projectTechnologies} {projectLinks} bind:showProject />
