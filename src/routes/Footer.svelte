<script>
    import { fly, fade } from 'svelte/transition';
  </script>
  
  <style>
    .floating {
      animation: float 3s ease-in-out infinite;
    }
  
    @keyframes float {
      0% {
        transform: translateY(0px);
      }
      50% {
        transform: translateY(-15px);
      }
      100% {
        transform: translateY(0px);
      }
    }
  </style>
  
  <section class="relative py-16 bg-gradient-to-r from-blue-700 to-green-700 text-white text-center overflow-hidden">
    <div class="absolute top-0 left-0 w-full h-full bg-black opacity-25"></div>
    <!-- Floating background elements -->
    <div class="absolute top-10 left-10 w-16 h-16 bg-white rounded-full floating opacity-50"></div>
    <div class="absolute top-20 right-20 w-24 h-24 bg-green-300 rounded-full floating opacity-50"></div>
    <div class="absolute bottom-10 left-20 w-20 h-20 bg-blue-300 rounded-full floating opacity-50"></div>
    <div class="absolute bottom-20 right-10 w-12 h-12 bg-white rounded-full floating opacity-50"></div>
  
    <div class="container mx-auto px-4 relative z-10">
      <h2 in:fly={{ y: -50, duration: 800 }} out:fly={{ y: 50, duration: 800 }} class="text-4xl font-bold mb-4">Join the YDO Community</h2>
      <p in:fade={{ duration: 1000 }} out:fade={{ duration: 1000 }} class="text-xl mb-8">Find your perfect match today and start your journey with us.</p>
      <a href="/register" class="inline-block bg-white text-blue-700 px-6 py-3 rounded shadow-lg transform hover:scale-110 transition duration-300">
        Get Started
      </a>
    </div>
  </section>
  