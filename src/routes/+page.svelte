<script>

    // image imports if you are not doing dynamic loading

    import {onMount} from "svelte";

    let activeLink = ""; // keep track of current active link for styling
    const handleLinkClick = (link) => {
        activeLink = link; // Update the active link on click.
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
            src: 'II-Dust.png',
            alt: 'Tablets!',
            text: "We have numerous tablets, with either Android or Ubuntu installed"
        },

        {src: '/X-Art.png', alt: 'LED Panels', text: "Controllers, cables, panels, we got them all."},

    ];

    let currentImageIndex = 0;

    onMount(() => {
        console.log("woo");
        const interval = setInterval(() => {
            currentImageIndex = (currentImageIndex + 1) % images.length;
            currentCallToAction = (currentCallToAction + 1) % callToAction.length;
        }, 3000);
    })

</script>

<svelte:head>
    <title>Playa Tarot</title>
</svelte:head>
<nav>
    <ul>
        <li class:active={activeLink === "project"}>
            <a href="/project" on:click={() => handleLinkClick("project")}>Project</a>
        </li>
        <li class:active={activeLink === "fundraiser"}>
            <a href="/fundraiser" on:click={() => handleLinkClick("fundraiser")}>Fundraiser</a>
        </li>
        <li class:active={activeLink === "about"}>
            <a href="/about" on:click={() => handleLinkClick("about")}>About Us</a>
        </li>
    </ul>
</nav>

<main>

    <div class="hero-section flex">
        <div class="image-slider w-2/5">
            <div class="container my-5 justify-center items-center" style="margin-left: 10%;">
                <div class="row justify-content-center" style="max-height: 25%">
                    <div class="col-md-6">
                        <div class="card">
                            <div class="image-container">
                                <img style="" src={images[currentImageIndex].src} alt={images[currentImageIndex].alt}
                                     class="card-img-top animated-image">
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="hero-text w-3/5">
            <div class="relative isolate px-6 pt-14 lg:px-8">
                <div class="absolute inset-x-0 -top-40 -z-10 transform-gpu overflow-hidden blur-3xl sm:-top-80"
                     aria-hidden="true">
                    <div
                        class="relative left-[calc(50%-11rem)] aspect-[1155/678] w-[36.125rem] -translate-x-1/2 rotate-[30deg] bg-gradient-to-tr from-[#ff80b5] to-[#9089fc] opacity-30 sm:left-[calc(50%-30rem)] sm:w-[72.1875rem]"
                        style="clip-path: polygon(74.1% 44.1%, 100% 61.6%, 97.5% 26.9%, 85.5% 0.1%, 80.7% 2%, 72.5% 32.5%, 60.2% 62.4%, 52.4% 68.1%, 47.5% 58.3%, 45.2% 34.5%, 27.5% 76.7%, 0.1% 64.9%, 17.9% 100%, 27.6% 76.8%, 76.1% 97.7%, 74.1% 44.1%)"></div>
                </div>
                <div class="mx-auto max-w-2xl py-32 sm:py-48 lg:py-56">
                    <div class="text-center">
                        <h1 class="text-balance text-5xl font-semibold tracking-tight text-gray-900 sm:text-7xl">Playa
                            Tarot</h1>
                        <p class="mt-8 text-pretty text-lg font-medium text-gray-500 sm:text-xl/8">An open art/gifting
                            project for Burning Man 2025</p>

                        <div class="hero-text w-3/5 flex">
                            <div class="w-1/3 flex flex-col justify-center items-center p-4">
                                <a
                                    href="/"
                                    class="bg-indigo-600 text-white font-semibold py-2 px-4 rounded hover:bg-indigo-700 transition duration-300"
                                >
                                    {callToAction[currentCallToAction].action}
                                </a>
                            </div>

                            <div class="w-2/3 p-4 transition-opacity duration-500"
                                 class:fade-in={currentCallToAction !== undefined}>
                                <p class="text-lg text-gray-700">
                                    {currentCallToAction !== undefined && callToAction[currentCallToAction].cot}

                            </div>
                        </div>
                            <p>
        Playa Tarot is a unique set of 72 tarot cards with images and themes
        from the event - currently done by @Reptar but you can make them your own.  Individual cards can be adopted with original artwork or you can help us
                                print them by a donation.
                                <p>
                        <b></b>
                        <i>All artwork is CC-BY-NC-SA-4.0 - use all you like, tattoo it on your butt if you want.  But for-profit use is forbidden.
                        </i></p>



                    </div>
                </div>
                <div
                    class="absolute inset-x-0 top-[calc(100%-13rem)] -z-10 transform-gpu overflow-hidden blur-3xl sm:top-[calc(100%-30rem)]"
                    aria-hidden="true">
                    <div
                        class="relative left-[calc(50%+3rem)] aspect-[1155/678] w-[36.125rem] -translate-x-1/2 bg-gradient-to-tr from-[#ff80b5] to-[#9089fc] opacity-30 sm:left-[calc(50%+36rem)] sm:w-[72.1875rem]"
                        style="clip-path: polygon(74.1% 44.1%, 100% 61.6%, 97.5% 26.9%, 85.5% 0.1%, 80.7% 2%, 72.5% 32.5%, 60.2% 62.4%, 52.4% 68.1%, 47.5% 58.3%, 45.2% 34.5%, 27.5% 76.7%, 0.1% 64.9%, 17.9% 100%, 27.6% 76.8%, 76.1% 97.7%, 74.1% 44.1%)"></div>
                </div>
            </div>
        </div>
    </div>


    <div class="bg-white">
        <header class="absolute inset-x-0 top-0 z-50">
            <nav class="flex items-center justify-between p-6 lg:px-8" aria-label="Global">
                <div class="flex lg:flex-1">
                </div>
                <div class="flex lg:hidden">
                </div>
                <div class="hidden lg:flex lg:gap-x-12">
                    <a href="/create" class="text-sm/6 font-semibold text-gray-900">Create</a>
                    <a href="/participate" class="text-sm/6 font-semibold text-gray-900">Participate</a>
                    <a href="/donate" class="text-sm/6 font-semibold text-gray-900">Donate</a>
                    <a href="https://thatcatcamp.com" class="text-sm/6 font-semibold text-gray-900">CAT Camp</a>
                </div>
            </nav>
            <!-- Mobile menu, show/hide based on menu open state. -->
            <div class="lg:hidden" role="dialog" aria-modal="true">
                <!-- Background backdrop, show/hide based on slide-over state. -->
                <div class="fixed inset-0 z-50"></div>
                <div
                    class="fixed inset-y-0 right-0 z-50 w-full overflow-y-auto bg-white px-6 py-6 sm:max-w-sm sm:ring-1 sm:ring-gray-900/10">
                    <div class="flex items-center justify-between">
                        <button type="button" class="-m-2.5 rounded-md p-2.5 text-gray-700">
                            <span class="sr-only">Close menu</span>
                            <svg class="size-6" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor"
                                 aria-hidden="true" data-slot="icon">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M6 18 18 6M6 6l12 12"/>
                            </svg>
                        </button>
                    </div>
                    <div class="mt-6 flow-root">
                    </div>
                </div>
            </div>
        </header>


    </div>


</main>

<style>


    nav {
        background-color: #f0f0f0; /* Example background color */
        padding: 10px;
        /* Other toolbar styles (e.g., border, shadow, etc.) */
    }

    nav ul {
        list-style: none; /* Remove bullet points */
        margin: 0;
        padding: 0;
        display: flex; /* Arrange list items horizontally */

    }

    nav li {
        margin-right: 20px; /* Spacing between list items */
    }

    nav li.active a { /* Style for the currently active link */
        font-weight: bold;
        text-decoration: underline; /* or any other distinctive style */

    }

    nav a {
        text-decoration: none; /* Remove underlines from links */
        color: #333; /* Example link color */
    }

    nav a:hover { /* Style on hover */
        color: #6366f1;
    }


    * {
        box-sizing: border-box
    }


    .active{
        background-color: #717171;
    }


    @keyframes fade {
        from {
            opacity: .4
        }
        to {
            opacity: 1
        }
    }

    img, button {
        position: absolute;
        background: #6366f1;
        max-height: 100%;
    }

    .hero-section {
        background-size: cover;
        background-position: center;
    }

    .animated-image {
        transition: opacity 0.5s ease-in-out;
    }

    main {
        padding-top: 56px;
    }

    .image-container {
        position: relative;
        width: 50%;
        padding-top: 75%; /* This sets the height to 25% of the width */
        overflow: hidden;
    }

    .image-container img {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    .fade-in {
        opacity: 1;
    }

    .hero-text > div { /* target direct children only - not nested elements in Slidy */
        opacity: 1; /* Start with elements hidden */
        transition: opacity 0.5s ease-in-out; /* Smooth transition */
    }
</style>
