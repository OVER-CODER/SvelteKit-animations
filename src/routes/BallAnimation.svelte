<script lang="ts">
    import { onMount } from 'svelte';
  
    let canvas: HTMLCanvasElement;
    let ctx: CanvasRenderingContext2D;
    let balls: Ball[] = [];
  
    onMount(() => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
      ctx = canvas.getContext('2d')!;
      createBalls();
      animate();
    });
  
    function createBalls() {
      for (let i = 0; i < 7; i++) {
        balls.push(new Ball());
      }
    }
  
    function animate() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      balls.forEach(ball => ball.update());
      requestAnimationFrame(animate);
    }
  
    class Ball {
      radius: number;
      x: number;
      y: number;
      dx: number;
      dy: number;
      color: string;
  
      constructor() {
        this.radius = 50;
        this.x = Math.random() * (canvas.width - this.radius * 2) + this.radius;
        this.y = Math.random() * (canvas.height - this.radius * 2) + this.radius;
        this.dx = (Math.random() - 0.5) * 4;
        this.dy = (Math.random() - 0.5) * 4;
        this.color = `hsl(${Math.random() * 360}, 100%, 50%)`;
      }
  
      draw() {
        ctx.beginPath();
        ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2, false);
        ctx.fillStyle = this.color;
        ctx.fill();
        ctx.closePath();
      }
  
      update() {
        if (this.x + this.radius > canvas.width || this.x - this.radius < 0) {
          this.dx = -this.dx;
        }
  
        if (this.y + this.radius > canvas.height || this.y - this.radius < 0) {
          this.dy = -this.dy;
        }
  
        this.x += this.dx;
        this.y += this.dy;
  
        this.draw();
      }
    }
  </script>
  
  <canvas bind:this={canvas} class="fixed top-0 left-0 w-full h-full z-0"></canvas>
  
  <style>
    canvas {
      background: #ffe4e1; /* Light pink background */
    }
  </style>
  