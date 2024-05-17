<script>
    import { fly } from 'svelte/transition';
  </script>
  
  <section class="py-16 bg-gray-100 text-gray-700">
    <div class="container mx-auto px-4">
      <h2 class="text-3xl font-bold text-center mb-12">Ready to find your match!</h2>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <div in:fly={{ x: -200, duration: 500 }} out:fly={{ x: 200, duration: 500 }} class="p-6 bg-white rounded-lg shadow-lg hover:shadow-2xl transform hover:-translate-y-2 transition">
          <h3 class="text-xl font-semibold mb-4">Choose Partner</h3>
          <p>You will get to choose 5 of your loved ones. Make your selection wisely to find your best match.</p>
        </div>
        <div in:fly={{ x: 0, duration: 500 }} out:fly={{ x: 0, duration: 500 }} class="p-6 bg-white rounded-lg shadow-lg hover:shadow-2xl transform hover:-translate-y-2 transition">
          <h3 class="text-xl font-semibold mb-4">Partner's Time</h3>
          <p>Wait for your partner to choose you too! Once both partners have chosen, it's a match.</p>
        </div>
        <div in:fly={{ x: 200, duration: 500 }} out:fly={{ x: -200, duration: 500 }} class="p-6 bg-white rounded-lg shadow-lg hover:shadow-2xl transform hover:-translate-y-2 transition">
          <h3 class="text-xl font-semibold mb-4">It's Matched</h3>
          <p>Check out our matched section to see whom you are matched with. Start connecting and build a relationship.</p>
        </div>
      </div>
    </div>
  </section>
  