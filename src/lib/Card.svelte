<script>
    import '@material/web/button/filled-button.js'

    export let title = "Card Title";
    export let content = "Card Content";
    export let image = "https://picsum.photos/2000/3000";
    export let thumbnail = "https://firebasestorage.googleapis.com/v0/b/seailz-pf.appspot.com/o/seailz_lmao_96x.webp?alt=media&token=80f2e399-2363-49f8-94c5-3b71f9e4562b"
    export let isAboutMeCard = false;
    export let hasThumbnail = true;
    export let id = "card"
    export let deselected = false;

    function linkDiscord() {
        window.open("https://discord.com/users/947691195658797167");
    }
</script>

<div id="{id}" class="card card_container" style="{deselected ? "transform: scale(0.3); margin-left:600px;" : ""}">
    <div class="card-image">
        <img src={image} alt="card img" />
    </div>
    <div class="card_top">
        <div class="card-title">
            <h1>{title}</h1>
        </div>
        {#if hasThumbnail}
        <div class="card-thumbnail">
            <img width="96" src={thumbnail} alt="card thumbnail">
        </div>
        {/if}
    </div>
    <div class="card-content">
        {@html content}
    </div>

    {#if isAboutMeCard}
        <md-filled-button class="button" on:click={linkDiscord}>
            <slot>Contact</slot>
        </md-filled-button>
    {/if}
</div>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Noto+Sans:wght@600&family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap');
    .button {
        position: absolute;
        bottom: 16px;
        right: 16px;
    }

    .card {
        background-color: rgb(0, 0, 0);
        width: 400px;
        height: 450px;
        border-radius: 24px;
        box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.75);
        transition: all 0.5s cubic-bezier(0.2, 0.0, 0, 1.0);
        color: white;
    }

    .card-thumbnail {
        position: absolute;
        right: 10%;
        top: 35%;
        outline: 8px solid black;
        border-radius: 50%;
    }

    .card-content {
        margin-left: 16px;
        color: rgb(222, 222, 222);
    }

    .card-title h1 {
        margin-bottom: 4px;
    }

    .card-title {
        margin-left: 16px;
    }

    .card-image {
        width: 100%;
        height: 45%;
        border-radius: 24px;
        object-fit: cover;
        overflow: hidden;
    }

    .card-image img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        overflow: hidden;
        border-radius: 24px;
    }

    .card:hover {
        box-shadow: 0px 0px 30px 0px rgba(0, 0, 0, 0.75);
        transform: scale(1.01);
    }

    @media (max-width: 480px) {
        .card {
            width: 300px;
            height: 400px;
            margin-top: 40px;
        }
    }
</style>