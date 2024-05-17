<script>
  import { slide } from 'svelte/transition';
    import Header from './Header.svelte';
</script>

<style>
  .floating-heart {
    animation: float 3s ease-in-out infinite;
  }

  .slide-in {
    animation: slideIn 1s ease-out;
  }

  @keyframes float {
    0% {
      transform: translateY(0px);
    }
    50% {
      transform: translateY(-20px);
    }
    100% {
      transform: translateY(0px);
    }
  }

  @keyframes slideIn {
    from {
      opacity: 0;
      transform: translateX(-50px);
    }
    to {
      opacity: 1;
      transform: translateX(0);
    }
  }
  .glass-nav {
    background-color: rgba(255, 255, 255, 0.1); /* Background color with transparency */
    backdrop-filter: blur(10px); /* Blurring effect */
  }
</style>

<div class="bg-gradient-to-r from-violet-800 to-pink-900 bg-opacity-50 text-white p-4 flex justify-between items-center rounded-lg shadow-lg glass-nav">
  <div class="text-2xl font-bold">YDO</div>
  <nav class="space-x-4">
    <a href="/" class="text-lg hover:text-gray-300">Login</a>
    <a href="/" class="text-lg hover:text-gray-300">Register</a>
  </nav>
</div>

<section class="h-[70svh] bg-gradient-to-r from-violet-700 to-pink-600 flex flex-col items-start justify-center text-white text-left p-8 relative ">
  <!-- Background floating elements -->
  <div class="absolute top-48 left-35 w-24 h-24 bg-white rounded-full floating-heart opacity-50"></div>
  <div class="absolute top-0 left-64 w-24 h-24 bg-white rounded-full floating-heart opacity-50"></div>
  <div class="absolute top-80 right-80 w-24 h-24 bg-violet-200 rounded-full floating-heart opacity-50"></div>
  <div class="absolute top-20 right-40 w-24 h-24 bg-pink-300 rounded-full floating-heart opacity-50"></div>
  <div class="absolute bottom-10 left-20 w-20 h-20 bg-violet-500 rounded-full floating-heart opacity-50"></div>
  <div class="absolute bottom-20 right-10 w-12 h-12 bg-white rounded-full floating-heart opacity-50"></div>

  <!-- Hero content -->
  <div in:slide={{ duration: 800 }} class="mb-8 slide-in">
    <h1 class="text-5xl font-bold mb-4">Find Your Perfect Match</h1>
    <p class="text-xl mb-6">Exclusively for IIITDMJ students</p>
    <div class="flex space-x-4">
      <a href="/login" class="bg-white text-pink-700 px-4 py-2 rounded shadow hover:bg-gray-200 transition duration-300 transform hover:scale-105">
        Login
      </a>
      <a href="/register" class="bg-white text-pink-700 px-4 py-2 rounded shadow hover:bg-gray-200 transition duration-300 transform hover:scale-105">
        Register
      </a>
    </div>
  </div>
</section>
