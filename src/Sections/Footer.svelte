<script>
    import { language } from "../store";
    let languageSelected;
    const unsubscribe = language.subscribe((val) => (languageSelected = val));
</script>

<section id="footer">
    <p>{["¡Contactame!", "Contact me!"][languageSelected]}</p>
    <a href="https://github.com/Onassis-Salinas"><img src="/Logos/Github.svg" alt="" /></a>
    <a href="https://www.facebook.com/people/Onassis-developer/61550880837299/"><img src="/Logos/Facebook.svg" alt="" /></a>
    <a href="https://www.instagram.com/onassis_developer/"> <img src="/Logos/Instagram.svg" alt="" /></a>
    <a href="wa.link/5zxn4t"> <img src="/Logos/Whatsapp.svg" alt="" /></a>
    <a href="mailto:onassis.dev@gmail.com"><img src="/Logos/Mail.svg" alt="" /></a>
    <p class="footer-text">{["Diseñado y programado por Onassis Salinas", "Designed and coded by Onassis Salinas"][languageSelected]}</p>
</section>

<style>
    section {
        width: 100%;
        display: flex;
        justify-content: center;
        gap: 10px;
        flex-wrap: wrap;
        margin-top: 50px;
        margin-bottom: 0;
    }
    img {
        width: 60px;
        aspect-ratio: 1;
    }
    p {
        width: 100%;
        text-align: center;
        margin: 0;
    }
    .footer-text {
        margin: 0 0 20px 0;
    }

    @media (max-width: 400px) {
        img {
            width: 45px;
        }
    }
</style>
