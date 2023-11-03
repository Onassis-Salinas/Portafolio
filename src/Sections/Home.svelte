<script>
    import SelectLanguage from "../Components/SelectLanguage.svelte";
    import { language } from "../store";
    let languageSelected;
    const unsubscribe = language.subscribe((val) => (languageSelected = val));

    const letters = "AbCDeGFhIJkLMNoPQrSTUvWXYz";

    const texts = [
        ["Hola, soy Onassis Salinas", "Hi, Im Onassis Salinas"],
        // ["dasdasd asd asd asd sadssadas as ", "asdasdas d asd asd as dsad as"],
    ];

    $: finaltext = texts[0][languageSelected];
    let text = "";

    let iteration = 0;
    let time = 80;
    setInterval(() => {
        time = 1;
        iteration += 1;
        text = finaltext
            .split("")
            .map((element, i) => {
                if (iteration - 15 > i) return finaltext[i];

                return element === " " ? " " : letters[Math.floor(Math.random() * 26)];
            })
            .join("");
    }, time);
</script>

<section>
    <SelectLanguage />
    <h1>{text}</h1>
    <p>{["Un desarrollador apasionado en busca de nuevos proyectos", "A passionate developer searching for new projects"][languageSelected]}</p>
    <img src="/down.svg" alt="" id="down-arrow" />
</section>

<style>
    section {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        min-height: calc(100lvh - 50px);
        margin: 0;
        margin-top: 50px;
    }
    h1 {
        font-family: var(--font2);
        font-size: var(--fs5);
        text-align: center;
        margin: 10px;
    }
    p {
        font-size: var(--fs3);
    }

    #down-arrow {
        position: absolute;
        transform: translateX(-50%);
        left: 50%;
        bottom: 20px;
        width: 100px;
        aspect-ratio: 1;
        animation: up-down 1s ease-in-out infinite;
    }

    @media (max-width: 600px) {
        p {
            text-align: center;
        }
    }

    @keyframes up-down {
        0% {
            transform: translate(-50%, 0);
        }
        50% {
            transform: translate(-50%, -20px);
        }
        100% {
            transform: translate(-50%, 0);
        }
    }
</style>
