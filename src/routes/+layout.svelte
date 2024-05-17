<script>
    import Header from './Header.svelte';
    import Footer from './Footer.svelte';
    import '../app.css';
  </script>
  
  <svelte:head>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
    
  </svelte:head>

  <main class="flex-grow">
    <slot />
  </main>
  <Footer />
  