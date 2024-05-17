<script lang="ts">
    import { onMount } from 'svelte';
  
    let canvas: HTMLCanvasElement;
    let ctx: CanvasRenderingContext2D;
  
    onMount(() => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
      ctx = canvas.getContext('2d')!;
      animate();
    });
  
    function drawWave(amplitude: number, frequency: number, phase: number, color: string) {
      ctx.beginPath();
      ctx.moveTo(0, canvas.height / 2);
  
      for (let x = 0; x < canvas.width; x++) {
        const y = canvas.height / 2 + amplitude * Math.sin((x + phase) * frequency);
        ctx.lineTo(x, y);
      }
  
      ctx.strokeStyle = color;
      ctx.stroke();
    }
  
    let phase = 0;
    function animate() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
  
      drawWave(30, 0.02, phase, 'rgba(255, 105, 180, 0.6)'); // Light pink
      drawWave(20, 0.03, phase + 50, 'rgba(255, 20, 147, 0.6)'); // Deep pink
      drawWave(40, 0.01, phase + 100, 'rgba(255, 182, 193, 0.6)'); // Light pink
  
      phase += 1;
      requestAnimationFrame(animate);
    }
  </script>
  
  <canvas bind:this={canvas} class="fixed top-0 left-0 w-full h-full z-0"></canvas>
  
  <style>
    canvas {
      background: #ffe4e1; /* Light pink background */
    }
  </style>
  