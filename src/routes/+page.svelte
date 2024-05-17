<script>
    import BallAnimation from './BallAnimation.svelte';
    import MovingWaves from './MovingWaves.svelte';
    import FillingWaves from './FillingWaves.svelte';
  </script>

  
  <div class="relative flex flex-col items-center justify-center min-h-screen text-center font-sans bg-pink-100">
    <!-- <BallAnimation /> -->
    <!-- <MovingWaves /> -->
    <FillingWaves />
    <div class="z-10 flex items-center justify-center gap-10 mb-10">
      <div>
        <h1 class="text-6xl font-bold text-violet-600">HEY</h1>
        <h1 class="text-6xl font-bold text-black">YOU</h1>
      </div>
      <div>
        <h1 class="text-6xl font-bold text-black">MEET</h1>
        <h1 class="text-6xl font-bold text-violet-600 ">YOU</h1>
      </div>
    </div>
    <div class="z-10">
      <img
        src="path/to/your/image.png"
        alt="Jumping character"
        class="w-64 h-auto mb-10"
      />
    </div>
    <div class="z-10 flex gap-10">
      <button class="px-6 py-3 text-white bg-pink-600 rounded-lg">GET STARTED</button>
      <button class="px-6 py-3 text-pink-600 border border-pink-600 rounded-lg">HOW IT WORKS</button>
    </div>
  </div>
  