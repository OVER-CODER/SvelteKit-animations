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
    function drawWave(amplitude: number, frequency: number, phase: number, color: string, fillHeight: number) {
        ctx.beginPath();
        ctx.moveTo(0, fillHeight);

        for (let x = 0; x < canvas.width; x++) {
            const y = canvas.height - fillHeight - amplitude * Math.sin((x + phase) * frequency); // Negate y to reverse direction
            ctx.lineTo(x, y);
        }

        ctx.lineTo(canvas.width, 0);
        ctx.lineTo(0, 0);
        ctx.closePath();
        ctx.fillStyle = color;
        ctx.fill();
    }

    let phase = 0;
    let fillHeight = 0;
    let animationspeed = 3;
    function animate() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
  
      drawWave(50, 0.01, phase, 'rgba(186, 85, 211, 0.6)', fillHeight*0.97);
      drawWave(50, 0.01, -phase + 20 , 'rgba(219, 112, 147, 0.6)', fillHeight*0.9);
      drawWave(30, 0.01, phase + 50, 'rgba(219, 112, 147, 0.6)', fillHeight*0.84); 

  
      phase += 1;
      if (fillHeight < canvas.height) {
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
  



   <!-- <script lang="ts">
    import { createEventDispatcher } from 'svelte';
    export let canvas: HTMLCanvasElement;
    let ctx: CanvasRenderingContext2D;
    let phase = 0;
    let fillHeight = 0;
    let animationspeed = 3;

    const dispatch = createEventDispatcher();

    function drawWave(amplitude: number, frequency: number, phase: number, color: string, fillHeight: number) {
        ctx.beginPath();
        ctx.moveTo(0, fillHeight);

        for (let x = 0; x < canvas.width; x++) {
            const y = canvas.height - fillHeight - amplitude * Math.sin((x + phase) * frequency);
            ctx.lineTo(x, y);
        }

        ctx.lineTo(canvas.width, 0);
        ctx.lineTo(0, 0);
        ctx.closePath();
        ctx.fillStyle = color;
        ctx.fill();
    }

    canvas.addEventListener('drawWaves', (event) => {
        ctx = event.detail;

        drawWave(50, 0.01, phase, 'rgba(186, 85, 211, 0.6)', fillHeight * 0.97);
        drawWave(50, 0.01, -phase + 20, 'rgba(219, 112, 147, 0.6)', fillHeight * 0.9);
        drawWave(30, 0.01, phase + 50, 'rgba(219, 112, 147, 0.6)', fillHeight * 0.84);

        phase += 1;
        if (fillHeight < canvas.height) {
            fillHeight += 1 * animationspeed;
        } else {
            dispatch('wavesFinished');
        }
    });
</script> -->
