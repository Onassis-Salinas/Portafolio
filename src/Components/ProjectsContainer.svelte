<script>
    export let languageSelected;
    export let projectSection;
    export let selectProject;
    let left = 0;
    let initialPosition = 0;
    let mousePosition = 0;
    let clicking = false;
    let div;
    let container;
    let sliderWidth = 0;
    let containerWidth = 0;
    $: if (div) sliderWidth = div.offsetWidth;
    $: if (div) containerWidth = container.offsetWidth;

    const unclickig = () => (clicking = false);

    const click = () => {
        clicking = true;
        initialPosition = mousePosition;
    };

    const mouseMove = (xPos) => {
        mousePosition = xPos;
        if (clicking) {
            const result = (mousePosition - initialPosition) * 1.5;

            if (left + result <= 0 && left + result > -(sliderWidth - containerWidth)) {
                left += result;
            }

            initialPosition = mousePosition;
        }
    };

    window.addEventListener("mousemove", (event) => mouseMove(event.clientX));
    window.addEventListener("mouseup", unclickig);
</script>

<h3>{projectSection.title[languageSelected]}</h3>
<div class="projects-container" bind:this={container}>
    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <div class="slider" style="left:{left}px" on:mousedown={click} bind:this={div}>
        {#each projectSection.projects as project}
            <!-- svelte-ignore a11y-click-events-have-key-events -->
            <!-- svelte-ignore a11y-no-static-element-interactions -->
            <div class="project">
                <!-- <img src={project.image} alt="" /> -->
                <div class="img" style="background-image:url({project.image})" on:click={() => selectProject(project.title, project.index)} />
                <p>{project.title[languageSelected]}</p>
            </div>
        {/each}
    </div>
</div>

<style>
    .projects-container {
        position: relative;
        display: flex;
        align-items: flex-start;
        overflow: hidden;
        height: 280px;
        user-select: none;
    }
    .slider {
        height: 100%;
        position: absolute;
        display: flex;
        align-items: flex-start;
        align-self: flex-start;
        gap: 10px;
        cursor: e-resize;
    }
    .project {
        flex-shrink: 0;
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 10px;
        background-color: var(--fc);
        border-radius: var(--br);
        width: 400px;
    }
    p {
        margin: 0;
        margin-top: 5px;
    }
    .img {
        width: 90%;
        cursor: pointer;
        aspect-ratio: 16/9;
        background-size: cover;
        background-position: center;
    }

    @media (hover: none) {
        .slider {
            position: static;
        }
        .projects-container {
            position: relative;
            overflow-x: auto;
            align-items: flex-start;
            justify-content: flex-start;
        }
    }
</style>
