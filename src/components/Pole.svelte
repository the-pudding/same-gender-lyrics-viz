<script>
    import { onMount } from 'svelte';
    import { fly } from "svelte/transition";
    import Icon from "./helpers/Icon.svelte";
    import {select} from "d3";

    let y;
    let padPos = 200;
</script>

<svelte:window bind:scrollY={y} />

<section id="pole">
    <div>
        <div class="line"></div>
        <div class="lil-nas-x">
            <div transition:fly="{{ y: -200, duration: 1000 }}" class="bubble">
                <p class="text">can’t believe i haven’t said bussy in a song yet. something has to be done about this.</p>
                <p class="credit"><a href="https://twitter.com/LilNasX/status/1397356243560255489?s=20" target=_blank>Lil Nas X on <Icon name="twitter" /></a></p>
            </div>
        </div>
    </div>
</section>

<style>
    #pole {
        position: fixed;
        top: 0;
        right: 6rem;
        z-index: 999;
        height: 100vh;
    }

    div {
        position: relative;
    }

    .full-height {
        height: 100vh; 
    }

    .line {
        position: absolute;
        width: 6px;
        height: 0;
        background-image: linear-gradient(90deg, var(--gray), var(--gray-light), var(--gray), var(--gray-dark), var(--gray), var(--gray-light), var(--gray));
        transition: height 0.5s ease-out;
    }

    .full-height {
        height: 100vh !important; 
    }

    .lil-nas-x {
        position: absolute;
        background: url("../assets/images/lilnasx_drawing.png") 0 0;
        background-size: cover;
        right: -78px;
        top: -400px;
        height: 150px;
        width: 150px;
        transition: top 1s ease-out;
    }

    .bubble {
        padding: 1rem;
        background-color: rgba(255, 255, 255, 0.7);
        position: absolute;
        left: -1rem;
        top: -80px;
        width: 110%;
        border-radius: 0.25rem;
        opacity: 0;
        transition: opacity 1s linear;
    }

    .bubble p {
        font-size: 0.75rem;
        margin: 0;
    }

    .credit {
        font-weight: 700;
    }

    .bubble:after {
        content: '';
        position: absolute;
        bottom: 0;
        left: 50%;
        width: 0;
        height: 0;
        border: 20px solid transparent;
        border-top-color: rgba(255, 255, 255, 0.7);
        border-bottom: 0;
        border-left: 0;
        margin-left: 40px;
        margin-bottom: -20px;
    }

    @keyframes poleCycle {
        100%   { background-position: 0 -450px ;}
    }

    .with-animation {
        animation: poleCycle 2s steps(3) infinite;
    }

    @media only screen and (max-width: 700px) {
        #pole {
            right: 4rem;
        }

        .line {
            width: 7px;
        }

        .lil-nas-x {
            right: -65px;
            height: 125px;
            width: 125px;
        }

        @keyframes poleCycle {
            100%   { background-position: 0 -375px ;}
        }

        .with-animation {
            animation: poleCycle 2s steps(3) infinite;
        }
    }

    @media only screen and (max-width: 400px) {
        #pole {
            right: 3.5rem;
        }

        .line {
            width: 5px;
        }

        .lil-nas-x {
            right: -52px;
            height: 100px;
            width: 100px;
        }

        .bubble {
            display:  none;
        }

        @keyframes poleCycle {
            100%   { background-position: 0 -300px ;}
        }

        .with-animation {
            animation: poleCycle 2s steps(3) infinite;
        }
    }
</style>