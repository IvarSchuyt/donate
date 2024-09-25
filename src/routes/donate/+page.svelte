<script>
    import { onMount } from 'svelte';

    let button;
    let links = [
        'https://donate.unrwa.org/gaza/~my-donation?_cv=1',
        'https://donate.unrwa.org/one-time/~my-donation',
        'https://donate.unrwa.org/keepuslearning/~my-donation',
        'https://crisisrelief.un.org/t/lebanon',
        'https://donate.unhcr.org/int/en/democratic-republic-congo-emergency',
        'https://www.warchild.org.uk/donate-democratic-republic-congo',
        'https://www.warchild.org.uk/',
        'https://crisisrelief.un.org/t/ukraine',
        'https://www.papuapartners.org/donate',
        'https://www.icrc.org/en/donate/sudan-crisis',
        'https://freetibet.org/',
        'https://uhrp.org/donate/',
        'https://donate.unhcr.org/int/en/south-sudan-emergency',
        'https://islamic-relief.org/appeals/yemen-crisis/',
        'https://hopeforhaiti.com/donate/',
        'https://crisisrelief.un.org/donate',
        'https://giving.unhcr.org/en/somalia/',
        'https://donate.unhcr.org/int/en/myanmar-situation',
        'https://www.islamic-relief.org.uk/where-we-work/country/bangladesh/',
        'https://www.care.org.au/country/papua-new-guinea/',
        'https://islamic-relief.org/appeals/syria-crisis/'
    ];

    function getRandomLink() {
        const randomIndex = Math.floor(Math.random() * links.length);
        return links[randomIndex];
    }

    function handleClick() {
        const randomLink = getRandomLink();
        window.open(randomLink, '_blank');
    }

    // Add event listener when the component is mounted
    onMount(() => {
        button.addEventListener('click', handleClick);

        // Clean up the event listener when the component is destroyed
        return () => {
            button.removeEventListener('click', handleClick);
        };
    });

    onMount(() => {
        const audio = new Audio('/audio2.mp3');
        audio.loop = true;
        audio.play();
    });
</script>

<section>
    <button bind:this={button}>Share your blessings</button>
</section>

<style>
    section {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
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