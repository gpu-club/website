<script>
    import { onMount } from 'svelte';

    let mobileMenuOpen = false;
    const toggleMenu = () => {
        mobileMenuOpen = !mobileMenuOpen;
    };

    let mouseX = 0;
    let mouseY = 0;
    let circleX = 0;
    let circleY = 0;

    const handleMouseMove = (event) => {
        mouseX = event.clientX;
        mouseY = event.clientY;
    };

    const updateCirclePosition = () => {
        circleX += (mouseX - circleX) * 0.1;
        circleY += (mouseY - circleY) * 0.1;

        requestAnimationFrame(updateCirclePosition);
    };

    onMount(() => {
        updateCirclePosition();
    });
</script>

<style>
    h1, h2, p {
        font-family: 'Nerd', sans-serif;
    }

    .bg-dark {
        background-color: black;
        color: #76ff03;
    }

    .bg-medd{
        background-color: #333;
        color: #76ff03;
    }

    .text-green {
        color: #76ff03;
    }

    .hover-green:hover {
        color: #58d700;
    }

    section {
        min-height: 100vh;
        display: flex;
        align-items: center;
        justify-content: center;
        position: relative;
        flex-direction: column; /* Ensure vertical stacking */
        text-align: center; /* Center text alignment */
        padding: 20px; /* Add padding for spacing */
    }

    .home-section {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        position: relative;
        z-index: 1;
        text-align: center;
    }

    .bg-video {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
        z-index: 0;
        opacity: 0.4;
    }

    .circle {
        width: 30px;
        height: 30px;
        border-radius: 50%;
        background-color: #76ff03;
        position: absolute;
        pointer-events: none;
        z-index: 3;
        transform: translate(-50%, -50%);
    }

    /* Responsive */
    @media (max-width: 768px) {
        .home-section {
            flex-direction: column;
        }
    }

    .event-card, .team-card {
        background-color: #2e2e2e;
        padding: 20px;
        border-radius: 10px;
        transition: transform 0.2s;
    }

    .event-card:hover, .team-card:hover {
        transform: scale(1.05);
    }

    .gallery-image {
        width: 100%;
        height: auto;
        border-radius: 10px;
    }

    /* Notification Styles */
    .notification {
        position: fixed;
        top: 20px;
        right: 20px;
        background-color: #76ff03;
        color: black;
        padding: 10px 20px;
        border-radius: 5px;
        z-index: 1000;
        transition: opacity 0.5s ease;
    }


</style>

<!-- Header -->
<header class="bg-dark py-6">
    <div class="container mx-auto flex justify-between items-center px-4">
        <h1 class="text-3xl sm:text-4xl font-bold">GPUG Club</h1>
        <nav>
            <ul class="hidden sm:flex space-x-6">
                <li><a href="#events" class="hover-green">Events</a></li>
                <li><a href="#team" class="hover-green">Team</a></li>
                <li><a href="#gallery" class="hover-green">Gallery</a></li>
                <li><a href="#contact" class="hover-green">Contact</a></li>
            </ul>
            <div class="sm:hidden">
                <button on:click={toggleMenu} class="text-green focus:outline-none">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path>
                    </svg>
                </button>
            </div>
        </nav>
    </div>

    {#if mobileMenuOpen}
    <div class="sm:hidden bg-dark">
        <ul class="space-y-4 py-4 px-6">
            <li><a href="#events" class="hover-green">Events</a></li>
            <li><a href="#team" class="hover-green">Team</a></li>
            <li><a href="#gallery" class="hover-green">Gallery</a></li>
            <li><a href="#contact" class="hover-green">Contact</a></li>
        </ul>
    </div>
    {/if}
</header>

<!-- Main Content -->
<main class="container mx-auto py-12 px-6 bg-dark" on:mousemove={handleMouseMove}>
    <!-- Home Section with video background and circle -->
    <section class="home-section">
        <h2 class="text-6xl mb-4">Welcome to GPUG Club</h2>
        <p class="text-2xl text-green">Where Innovation Meets Community</p>
    </section>

    <!-- Upcoming Events Section -->
    <section id="events" class="mb-12">
        <h2 class="text-4xl font-semibold mb-6">Upcoming Events</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
            <div class="event-card text-green">
                <h3 class="text-2xl font-bold mb-2">Hackathon 2024</h3>
                <p>Date: 15th March 2024</p>
                <p>Join us for a 48-hour coding challenge to solve real-world problems with innovation and creativity.</p>
            </div>
            <div class="event-card text-green">
                <h3 class="text-2xl font-bold mb-2">Tech Talk: Future of AI</h3>
                <p>Date: 5th February 2024</p>
                <p>Explore cutting-edge AI technologies with industry experts and get insights into the future of artificial intelligence.</p>
            </div>
            <div class="event-card text-green">
                <h3 class="text-2xl font-bold mb-2">Annual Meet-up</h3>
                <p>Date: 20th April 2024</p>
                <p>A celebration of our achievements and a discussion of the exciting future plans of the GPUG Club.</p>
            </div>
        </div>
    </section>

    <!-- Team Section -->
    <section id="team" class="mb-12">
        <h2 class="text-4xl font-semibold mb-6">Meet Our Team</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
            <div class="team-card text-green">
                <h3 class="text-2xl font-bold mb-2">Bhargav Gembali</h3>
                <p>Founder & President</p>
                <p>Driving the vision and growth of the GPUG Club.</p>
            </div>
            <div class="team-card text-green">
                <h3 class="text-2xl font-bold mb-2">John Doe</h3>
                <p>Vice President</p>
                <p>Leading event organization and community outreach.</p>
            </div>
            <div class="team-card text-green">
                <h3 class="text-2xl font-bold mb-2">Jane Smith</h3>
                <p>Head of Technology</p>
                <p>Overseeing technical initiatives and projects.</p>
            </div>
        </div>
    </section>

    <!-- Gallery Section -->
    <section id="gallery" class="mb-12">
        <h2 class="text-4xl font-semibold mb-6">Gallery</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
            <img src="https://via.placeholder.com/300" alt="Gallery Image 1" class="gallery-image" />
            <img src="https://via.placeholder.com/300" alt="Gallery Image 2" class="gallery-image" />
            <img src="https://via.placeholder.com/300" alt="Gallery Image 3" class="gallery-image" />
        </div>
    </section>

    <!-- Contact Us Section -->
    <section id="contact" class="mb-12">
        <h2 class="text-4xl font-semibold mb-6">Contact Us</h2>
        <form on:submit|preventDefault={sendMessage} class="max-w-md mx-auto">
            <div class="mb-4">
                <label for="name" class="block text-green">Name:</label>
                <input type="text"  id="name" required class="border border-gray-300 rounded-md w-full p-2" />
            </div>
            <div class="mb-4">
                <label for="email" class="block text-green">Email:</label>
                <input type="email"  id="email" required class="border border-gray-300 rounded-md w-full p-2" />
            </div>
            <div class="mb-4">
                <label for="message" class="block text-green">Message:</label>
                <textarea  id="message" required class="border border-gray-300 rounded-md w-full p-2" rows="4"></textarea>
            </div>
            <button type="submit" class="bg-green-500 text-white font-bold py-2 px-4 rounded">Send Message</button>
        </form>
    </section>

    

</main>

<!-- Footer -->
<footer class="bg-medd py-4">
    <div class="container mx-auto text-center">
        <p class="text-green">© 2024 GPUG Club. All rights reserved.</p>
    </div>
</footer>
