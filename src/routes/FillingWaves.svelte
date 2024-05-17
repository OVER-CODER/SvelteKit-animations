<script lang="ts">
    import { onMount } from 'svelte';
  
    let canvas: HTMLCanvasElement;
    let ctx: CanvasRenderingContext2D;
  
    onMount(() => {
      canvas.width = window.innerWidth;
        canvas.height = window.innerHeight - 50;
      ctx = canvas.getContext('2d')!;
      animate();
    });
    function drawWave(amplitude: number, frequency: number, phase: number, color: string, fillHeight: number) {
        ctx.beginPath();
        ctx.moveTo(0, fillHeight);

        for (let x = 0; x < canvas.width; x++) {
            const y = fillHeight - amplitude * Math.sin((x + phase) * frequency); // Negate y to reverse direction
            ctx.lineTo(x, y);
        }

        ctx.lineTo(canvas.width, 0); // Change to 0 to close the path at the top
        ctx.lineTo(0, 0); // Change to 0 to close the path at the top
        ctx.closePath();
        ctx.fillStyle = color;
        ctx.fill();
    }

    let phase = 0;
    let fillHeight = 0;
    let animationspeed = 3;
    function animate() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
  
      drawWave(60, 0.01, phase, 'rgba(186, 85, 211, 0.6)', fillHeight*0.72); // Darker Violet
drawWave(40, 0.01, -phase + 20 , 'rgba(219, 112, 147, 0.6)', fillHeight*0.6); // Darker Pink
drawWave(30, 0.01, phase + 50, 'rgba(219, 112, 147, 0.6)', fillHeight*0.55); // Pinkish violet

  
      phase += 1;
      if (fillHeight < 8*canvas.height/9) {
        fillHeight += 1*animationspeed;
      }
      requestAnimationFrame(animate);
    }
  </script>
  
  <canvas bind:this={canvas} class="fixed top-0 left-0 w-full h-full z-0"></canvas>
  
  <style>
    canvas {
      background: #ffe4e1; /* Light pink background */
    }
  </style>
  