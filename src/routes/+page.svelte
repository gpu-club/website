<script>
  import { onMount } from "svelte";

  let mobileMenuOpen = false;
  let isHoveringGPUG = false;

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

  const sendMessage = () => {
    // Simulate form submission or add your logic
    alert("Message sent!");
  };

  onMount(() => {
    updateCirclePosition();
  });

  const handleGPUGHover = (isHovering) => {
    isHoveringGPUG = isHovering;
  };
</script>

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
          <svg
            class="w-6 h-6"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M4 6h16M4 12h16m-7 6h7"
            ></path>
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
<main
  class="container mx-auto py-12 px-6 bg-dark"
  on:mousemove={handleMouseMove}
>
  <!-- Circle that follows the mouse -->

  <section class="home-section">
    <h2 class="text-6xl mb-4">
      Welcome to
      <span
        class="text-6xl mb-4 bg-glow"
        on:mouseenter={() => handleGPUGHover(true)}
        on:mouseleave={() => handleGPUGHover(false)}
      >
        GPUG
      </span>
      Club
    </h2>
    <p class="text-2xl text-green">Where Innovation Meets Community</p>
  </section>

  <!-- Circle that follows the mouse and changes color when hovering GPUG -->
  <div
    class="circle {isHoveringGPUG ? 'black' : ''}"
    style="left: {circleX}px; top: {circleY}px;"
  ></div>

  
  <!-- Events Section -->
<section id="events" class="my-12">
    <h2 class="text-4xl font-semibold mb-6">Upcoming Events</h2>
    <div class="space-y-4">
        <div class="p-4 border rounded-md bg-black-800 shadow-md">
            <h3 class="text-xl font-bold">Event Title 1</h3>
            <p class="text-gray-600">Date: January 1, 2024</p>
            <p class="text-gray-600">Location: Venue Name</p>
            <p class="mt-2">Description of the event goes here. Include any relevant details and information about what attendees can expect.</p>
        </div>
        <div class="p-4 border rounded-md bg-black-800 shadow-md">
            <h3 class="text-xl font-bold">Event Title 2</h3>
            <p class="text-gray-600">Date: February 15, 2024</p>
            <p class="text-gray-600">Location: Venue Name</p>
            <p class="mt-2">Description of the event goes here. Include any relevant details and information about what attendees can expect.</p>
        </div>
        <div class="p-4 border rounded-md bg-black-800  shadow-md">
            <h3 class="text-xl font-bold">Event Title 3</h3>
            <p class="text-gray-600">Date: March 10, 2024</p>
            <p class="text-gray-600">Location: Venue Name</p>
            <p class="mt-2">Description of the event goes here. Include any relevant details and information about what attendees can expect.</p>
        </div>
    </div>
</section>

  <!-- Team Section -->
  <section id="team" class="mb-12">
    <h2 class="text-4xl font-semibold mb-6">Meet Our Team</h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
      <div class="team-card text-green">
      <img src="/src/imgs/akshat.png" alt="Akshat Mangudi" class="team-image" />
        <h3 class="text-2xl font-bold mb-2">Akshat Mangudi</h3>
        <p>President</p>
        <p>Driving the vision and growth of the GPUG Club.</p>
      </div>
      <div class="team-card text-green">
      <img src="/src/imgs/kaviraj.png" alt="Kaviraj" class="team-image" />
        <h3 class="text-2xl font-bold mb-2">Kaviraj</h3>
        <p>Secretary</p>
        <p>Leading club and executing activites.</p>
      </div>
      <div class="team-card text-green">
      <img src="/src/imgs/bhargav.png" alt="Bhargav" class="team-image" />
        <h3 class="text-2xl font-bold mb-2">Bhargav Gembali</h3>
        <p>Technical team lead</p>
        <p>Overseeing technical projects and innovation.</p>
      </div>
      <div class="team-card text-green">
      <img src="Arya.jpg" alt="Arya" class="team-image" />
        <h3 class="text-2xl font-bold mb-2">Arya Komukula</h3>
        <p>Creative team lead</p>
        <p>Driving the vision and growth of the GPUG Club.</p>
      </div>
      <div class="team-card text-green">
      <img src="jones.jpg" alt="Jones" class="team-image" />
        <h3 class="text-2xl font-bold mb-2">Jones</h3>
        <p>Event Management Lead</p>
        <p>Leading club and executing activites.</p>
      </div>
      <div class="team-card text-green">
      <img src="yashaswini.jpg" alt="yashaswini" class="team-image" />
        <h3 class="text-2xl font-bold mb-2">Yashaswini</h3>
        <p>Outreach</p>
        <p>Overseeing technical projects and innovation.</p>
      </div>
    </div>
  </section>



  <!-- Gallery Section -->
  <section id="gallery" class="mb-12">
    <h2 class="text-4xl font-semibold mb-6">Gallery</h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
      <img src="image1.jpg" alt="Event 1" class="gallery-image" />
      <img src="image2.jpg" alt="Event 2" class="gallery-image" />
      <img src="image3.jpg" alt="Event 3" class="gallery-image" />
    </div>
  </section>

  <!-- Contact Section -->
  <section id="contact">
    <h2 class="text-4xl font-semibold mb-6">Contact Us</h2>
    <form class="space-y-4 text-green">
      <div>
        <label for="name" class="block mb-2">Your Name</label>
        <input
          type="text"
          id="name"
          class="w-full p-2 bg-medd rounded-md focus:outline-none focus:ring-2 focus:ring-green-600"
        />
      </div>
      <div>
        <label for="email" class="block mb-2">Your Email</label>
        <input
          type="email"
          id="email"
          class="w-full p-2 bg-medd rounded-md focus:outline-none focus:ring-2 focus:ring-green-600"
        />
      </div>
      <div>
        <label for="message" class="block mb-2">Message</label>
        <textarea
          id="message"
          class="w-full p-2 bg-medd rounded-md focus:outline-none focus:ring-2 focus:ring-green-600"
        ></textarea>
      </div>
      <button
        type="button"
        on:click={sendMessage}
        class="px-6 py-2  bg-green-400 text-black rounded-md"
        >Send Message</button
      >
    </form>
  </section>
</main>

<!-- Footer -->
<footer class="bg-dark py-6 text-center text-green">
  <p>&copy; 2024 GPUG Club. All rights reserved.</p>
</footer>

<style>
  /* Smooth Scrolling */
  html {
    scroll-behavior: smooth;
  }

  h1,
  h2,
  p {
    font-family: "Nerd", sans-serif;
  }

  .bg-dark {
    background-color: black;
    color: #76ff03;
  }

  .bg-medd {
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
    flex-direction: column;
    text-align: center;
    padding: 20px;
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

  .bg-glow {
    background: #76ff03;
    color: black;
    border-radius: 30px;
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

  /* Circle styling */
  .circle {
    width: 30px;
    height: 30px;
    border-radius: 50%;
    background-color: #76ff03;
    position: absolute;
    pointer-events: none;
    z-index: 3;
    transform: translate(-50%, -50%);
    transition: background-color 0.3s ease;
    transition: scale 0.3s ease;
  }

  .circle.black {
    background-color: black;
    scale:1.5;
  }

  /* Header styles */
  header {
    position: fixed;
    top: 0;
    width: 100%;
    background-color: black;
    z-index: 10;
  }

  /* Adjust page content for fixed header */
  main {
    margin-top: 80px; /* Adjust according to the header height */
  }

  /* Responsive */
  @media (max-width: 768px) {
    .home-section {
      flex-direction: column;
    }
  }

  .event-card,
  .team-card {
    background-color: #000000;
    padding: 20px;
    border-radius: 10px;
    transition: transform 0.2s;
  }

  .event-card:hover,
  .team-card:hover {
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
