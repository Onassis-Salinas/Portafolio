<script>
    import { language } from "../store";
    let languageSelected;
    const unsubscribe = language.subscribe((val) => (languageSelected = val));

    const letters = "AbCDeGFhIJkLMNoPQrSTUvWXYz";

    const texts = [
        ["Hola, soy Onassis Salinas", "Hi, Im Onassis Salinas"],
        // ["hola como estas ", "Hi how a re yopu"],
    ];

    $: finaltext = texts[0][languageSelected];
    let text = "";

    let iteration = 0;
    setInterval(() => {
        iteration += 1;
        text = finaltext
            .split("")
            .map((element, i) => {
                if (iteration - 15 > i) return finaltext[i];

                return element === " " ? " " : letters[Math.floor(Math.random() * 26)];
            })
            .join("");
    }, 40);
</script>

<section>
    <h1>{text}</h1>
    <p>{["Un programador apasionado en busca de nuevos proyectos", "A passionate programmer searching for new projects"][languageSelected]}</p>
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
</style>
