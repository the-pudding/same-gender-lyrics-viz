<script>
    import { onMount } from 'svelte';

    let y;
    let innerHeight;
    let padding = 200;
    let h;
    let triggerChapstick;

    onMount(() => {
		h = Math.max(
            document.body.clientHeight, 
            document.body.scrollHeight,
            document.body.offsetHeight
        );
	});
</script>

<section id="chapstick" style="height: {h}px;">
    <div class="stick animation"></div>
    <div class="stick animation"></div>
    <div class="stick animation"></div>
    <div class="stick animation"></div>
    <div class="stick animation"></div>
    <div class="stick animation"></div>
    <div class="stick animation"></div>
    <div class="stick animation"></div>
</section>

<style>
    #chapstick {
        position: absolute;
        pointer-events: none;
        width: 100%;
        display: flex;
        justify-content: space-around;
        flex-wrap: wrap;
        overflow-x: hidden;
        transition: opacity 0.25s linear;
    }

    .stick { 
        width: 200px;
        height: 63px;
        background-image: url("../assets/images/chapstick_drawing.png");
        background-repeat: no-repeat;
        background-size: contain;
        opacity: 0;
    }

    @media only screen and (max-width: 700px) {
        .stick {
            width: 150px;
            height: 48px;
        }
    }

    @media only screen and (max-width: 400px) {
        .stick {
            width: 100px;
            height: 32px;
        }
    }
</style>