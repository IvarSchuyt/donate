<script>
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';
    
    let audio;
    let video;
    let button;

    function playMedia() {
        audio.play();
        video.play();
    }

    function handleKeydown(event) {
        if (event.key === 'Enter') {
            playMedia();
            startRedirectTimer();
        }
    }

    function handleClick() {
        playMedia();
        startRedirectTimer();
    }

    function startRedirectTimer() {
        setTimeout(() => {
            goto('/donate');
        }, 18000);
    }

    // Add event listeners when the component is mounted
    onMount(() => {
        window.addEventListener('keydown', handleKeydown);
        button.addEventListener('click', handleClick);

        // Clean up the event listeners when the component is destroyed
        return () => {
            window.removeEventListener('keydown', handleKeydown);
            button.removeEventListener('click', handleClick);
        };
    });
</script>

<section>
    <video bind:this={video} src="website.mp4" preload="auto">
        <track kind="captions">
    </video>
    <audio bind:this={audio} src="/audio1.mp3" preload="auto"></audio>
    <button bind:this={button}>Enter</button>
</section>

<style>
    section {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }

    video {
        height: 100vh;
        width: 100vw;
        position: absolute;
    }

    button {
        padding: 10px 20px;
        background-color: #f00;
        color: #fff;
        border: none;
        border-radius: 5px;
        cursor: pointer;
        position: relative;
        z-index: 1;
    }
</style>