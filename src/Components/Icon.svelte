<script>
    export let route;
</script>

<img src={route} alt="" title={route.slice(6, -4)} />

<style>
    img {
        display: block;
        height: 80px;
        padding: 5px;
        background-color: var(--fc);
        border-radius: var(--br);
        aspect-ratio: 1/1;
        transition: all 0.2s ease;
    }
    img:hover {
        transform: translateY(-3px);
    }
    @media(max-width:600px){
        img{
            height: 70px;
        }
    }
    @media(max-width:400px){
        img{
            height: 50px;
        }
    }
</style>
