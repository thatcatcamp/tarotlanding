<script>
    import {onMount} from "svelte";
    import {fade} from 'svelte/transition';
    import {crossfade} from 'svelte/transition';
    import {quintOut} from 'svelte/easing';

    let activeLink = "";
    const handleLinkClick = (link) => {
        activeLink = link;
    };

    let callToAction = [
        {
            "action": "Create",
            "cot": "Sign up and create artwork for one or more cards!"
        },
        {
            "action": "Participate",
            "cot": "Host tarot readings at your camp or artwork"
        },
        {
            "action": "Donate",
            "cot": "Support us with funds to print and gift these cards"
        }
    ];
    let currentCallToAction = 0;

    let images = [
        {
            src: '/II-The+Sparklepony.png',
            alt: 'Laptops!',
            text: "We had a wide selection of laptops with Mint Linux preinstalled."
        },
        {
            src: 'X-The+Wheel.png',
            alt: 'Tablets!',
            text: "We have numerous tablets, with either Android or Ubuntu installed"
        },
        {
            src: 'V-Art.png',
            alt: 'Tablets!',
            text: "We have numerous tablets, with either Android or Ubuntu installed"
        },
        {
            src: 'c.png',
            alt: 'Tablets!',
            text: "We have numerous tablets, with either Android or Ubuntu installed"
        },
        {
            src: 'II-Dust.png',
            alt: 'Tablets!',
            text: "We have numerous tablets, with either Android or Ubuntu installed"
        },
        {
            src: '/X-Art.png',
            alt: 'LED Panels',
            text: "Controllers, cables, panels, we got them all."
        }
    ];

    let currentImageIndex = 0;
    // Create crossfade transition
    const [send, receive] = crossfade({
        duration: 600,
        easing: quintOut
    });
    onMount(() => {
        const interval = setInterval(() => {
            currentImageIndex = (currentImageIndex + 1) % images.length;
            currentCallToAction = (currentCallToAction + 1) % callToAction.length;
        }, 3000);

        // Cleanup interval on component destruction
        return () => clearInterval(interval);
    });
</script>

<svelte:head>
    <title>Playa Tarot</title>
</svelte:head>

<nav>
    <ul>
        <li class:active={activeLink === "project"}>
            <a href="/create" on:click={() => handleLinkClick("create")}>Create</a>
        </li>
        <li class:active={activeLink === "fundraiser"}>
            <a href="/donate" on:click={() => handleLinkClick("donate")}>Donate</a>
        </li>
        <li class:active={activeLink === "participate"}>
            <a href="/participate" on:click={() => handleLinkClick("participate")}>Participate</a>
        </li>

        <li class:active={activeLink === "about"}>
            <a href="https://thatcatcamp.com" on:click={() => handleLinkClick("about")}>About Us</a>
        </li>
    </ul>
</nav>

<main>
    <div class="hero-section flex flex-col md:flex-row">
        <div class="image-slider w-full md:w-2/5 px-4 md:px-0">
            <div class="container mx-auto my-5">
                <div class="flex justify-center items-center">
                    <div class="image-container">
                        {#key currentImageIndex}
                            <img
                                in:receive="{{ key: currentImageIndex }}"
                                out:send="{{ key: currentImageIndex }}"
                                src={images[currentImageIndex].src}
                                alt={images[currentImageIndex].alt}
                                class="absolute inset-0 w-full h-full object-contain"
                            />
                        {/key}
                    </div>

                </div>
            </div>
        </div>

        <div class="hero-text w-full md:w-3/5 px-4">
            <div class="text-center md:text-left">
                <h1 class="text-4xl md:text-5xl lg:text-7xl font-semibold tracking-tight text-gray-900 mb-4">
                    Playa Tarot
                </h1>

                <p class="text-lg font-medium text-gray-500 mb-6">
                    An open art/gifting project for Burning Man 2025
                </p>

                <div
                    class="flex flex-col md:flex-row items-center justify-center md:justify-start space-y-4 md:space-y-0 md:space-x-6">
                    <a
                        href="/"
                        class="bg-indigo-600 text-white font-semibold py-2 px-4 rounded hover:bg-indigo-700 transition duration-300"
                    >
                        {callToAction[currentCallToAction].action}
                    </a>

                    <p class="text-lg text-gray-700 text-center md:text-left">
                        {callToAction[currentCallToAction].cot}
                    </p>
                </div>

                <div class="mt-6 text-center md:text-left">
                    <p class="mb-4">
                        Playa Tarot is a unique set of 72 tarot cards with images and themes from the event - currently
                        done by @Reptar but you can make them your own. Individual cards can be adopted with original
                        artwork or you can help us print them by a donation.
                    </p>
                    <table class="w-full border-collapse">
                        <thead class="bg-gray-100">
                        <tr>
                            <th class="border p-2">Playa Suite</th>
                            <th class="border p-2">Theme/Style</th>
                        </tr>
                        </thead>
                        <tbody>
                        <tr class="hover:bg-gray-50">
                            <td class="border p-2">Shots</td>
                            <td class="border p-2">Cups, emotion, relationships.  Color theme is purple, romantic/heroic artwork.</td>
                        </tr>
                        <tr class="hover:bg-gray-50">
                            <td class="border p-2">Art</td>
                            <td class="border p-2">Wands - fire, action, creativity.  Dreamy, Art Nouveau style - yellow/dust color theme.</td>
                        </tr>
                        <tr class="hover:bg-gray-50">
                            <td class="border p-2">Rebar</td>
                            <td class="border p-2">Swords, communication, big sad. Theme is 1980-2000's book/magazine illustration.</td>
                        </tr>
                        <tr class="hover:bg-gray-50">
                            <td class="border p-2">Dust</td>
                            <td class="border p-2">Pentacles, earth, daily world.  Theme is 1950-1960's retro, washed colors and heavy on pastels.</td>
                        </tr>
                        </tbody>
                    </table>
                    <p class="italic text-sm">
                        <b>All artwork is CC-BY-NC-SA-4.0</b> - use all you like, tattoo it on your butt if you want.
                        But for-profit use is forbidden.
                    </p>
                </div>
            </div>
        </div>
    </div>
</main>

<style>
    /* Base Styles */
    * {
        box-sizing: border-box;
    }

    nav {
        background-color: #f0f0f0;
        padding: 10px;
        width: 100%;
    }

    nav ul {
        list-style: none;
        margin: 0;
        padding: 0;
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    @media (min-width: 768px) {
        nav ul {
            flex-direction: row;
            justify-content: center;
        }
    }

    nav li {
        margin: 10px 15px;
    }

    nav li.active a {
        font-weight: bold;
        text-decoration: underline;
    }

    nav a {
        text-decoration: none;
        color: #333;
    }

    nav a:hover {
        color: #6366f1;
    }

    .image-container {
        position: relative;
        width: 100%;
        max-width: 400px; /* Increased width */
        overflow: visible; /* Allow image to overflow if needed */
    }

    .image-container img {
        position: relative; /* Changed from absolute */
        width: 100%;
        height: auto; /* Auto height to maintain aspect ratio */
        object-fit: contain; /* Ensures entire image is visible */
        display: block; /* Remove any potential inline spacing */
    }

    .animated-image {
        transition: opacity 0.5s ease-in-out;
    }

    /* Responsive adjustments */
    @media (max-width: 768px) {
        .hero-section {
            text-align: center;
        }

        h1 {
            font-size: 2.5rem;
        }
    }

    .image-container {
        position: relative;
        width: 100%;
        max-width: 400px;
        height: 300px;
        overflow: hidden;
    }

    .image-container img {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        object-fit: contain;
    }
</style>
