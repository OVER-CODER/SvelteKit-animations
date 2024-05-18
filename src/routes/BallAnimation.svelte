<!-- <script lang="ts">
    import { onMount } from 'svelte';
    let canvaswaves: HTMLCanvasElement;
    let canvasballs: HTMLCanvasElement;
    let ctxwaves: CanvasRenderingContext2D;
    let ctxballs: CanvasRenderingContext2D;
    let balls: Ball[] = [];
  
    onMount(() => {
      canvasballs.width = window.innerWidth;
      canvasballs.height = window.innerHeight;
      canvaswaves.width = window.innerWidth;
      canvaswaves.height = window.innerHeight;
      ctxballs = canvasballs.getContext('2d')!;
      ctxwaves = canvaswaves.getContext('2d')!;
      createBalls();
      animateballs();
      animatewaves();
    });
  
    function createBalls() {
      for (let i = 0; i < 7; i++) {
        balls.push(new Ball());
      }
    }
  
    function animateballs() {
      ctxballs.clearRect(0, 0, canvasballs.width, canvasballs.height);
      balls.forEach(ball => ball.update());
      requestAnimationFrame(animateballs);
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
        this.x = Math.random() * (canvasballs.width - this.radius * 2) + this.radius;
        this.y = Math.random() * (canvasballs.height - this.radius * 2) + this.radius;
        this.dx = (Math.random() - 0.5) * 4;
        this.dy = (Math.random() - 0.5) * 4;
        this.color = `hsl(${Math.random() * 360}, 100%, 50%)`;
      }
  
      draw() {
        ctxballs.beginPath();
        ctxballs.arc(this.x, this.y, this.radius, 0, Math.PI * 2, false);
        ctxballs.fillStyle = this.color;
        ctxballs.fill();
        ctxballs.closePath();
      }
  
      update() {
        if (this.x + this.radius > canvasballs.width || this.x - this.radius < 0) {
          this.dx = -this.dx;
        }
  
        if (this.y + this.radius > canvasballs.height || this.y - this.radius < 0) {
          this.dy = -this.dy;
        }
  
        this.x += this.dx;
        this.y += this.dy;
  
        this.draw();
      }

    }
      function drawWave(amplitude: number, frequency: number, phase: number, color: string, fillHeight: number) {
        ctxwaves.beginPath();
        ctxwaves.moveTo(0, fillHeight);

        for (let x = 0; x < canvaswaves.width; x++) {
            const y = canvaswaves.height - fillHeight - amplitude * Math.sin((x + phase) * frequency); // Negate y to reverse direction
            ctxwaves.lineTo(x, y);
        }

        ctxwaves.lineTo(canvaswaves.width, 0);
        ctxwaves.lineTo(0, 0);
        ctxwaves.closePath();
        ctxwaves.fillStyle = color;
        ctxwaves.fill();
    }

    let phase = 0;
    let fillHeight = 0;
    let animationspeed = 3;
    function animatewaves() {
      ctxwaves.clearRect(0, 0, canvaswaves.width, canvaswaves.height);
  
      drawWave(50, 0.01, phase, 'rgba(186, 85, 211, 0.6)', fillHeight*0.97);
      drawWave(50, 0.01, -phase + 20 , 'rgba(219, 112, 147, 0.6)', fillHeight*0.9);
      drawWave(30, 0.01, phase + 50, 'rgba(219, 112, 147, 0.6)', fillHeight*0.84); 

  
      phase += 1;
      if (fillHeight < canvaswaves.height) {
        fillHeight += 1*animationspeed;
      }
      requestAnimationFrame(animatewaves);
    }
    
  </script>
  
  <canvas bind:this={canvasballs} class="fixed top-0 left-0 w-full h-full z-1"></canvas>
  <canvas bind:this={canvaswaves} class="fixed top-0 left-0 w-full h-full z-0"></canvas>
  
  <style>
    canvas {
      background: #ffe4e1; /* Light pink background */
    }
  </style>
   -->

   <script lang="ts">
    import { onMount } from 'svelte';
    let canvaswaves: HTMLCanvasElement;
    let canvasballs: HTMLCanvasElement;
    let ctxwaves: CanvasRenderingContext2D;
    let ctxballs: CanvasRenderingContext2D;
    let balls: Ball[] = [];
  
    onMount(() => {
      canvasballs.width = window.innerWidth;
      canvasballs.height = window.innerHeight;
      canvaswaves.width = window.innerWidth;
      canvaswaves.height = window.innerHeight;
      ctxballs = canvasballs.getContext('2d')!;
      ctxwaves = canvaswaves.getContext('2d')!;
      createBalls();
      animateballs();
      animatewaves();
    });
  
    function createBalls() {
      for (let i = 0; i < 7; i++) {
        balls.push(new Ball());
      }
    }
  
    function animateballs() {
      ctxballs.clearRect(0, 0, canvasballs.width, canvasballs.height);
      balls.forEach(ball => ball.update());
      requestAnimationFrame(animateballs);
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
        this.x = Math.random() * (canvasballs.width - this.radius * 2) + this.radius;
        this.y = Math.random() * (canvasballs.height - this.radius * 2) + this.radius;
        this.dx = (Math.random() - 0.5) * 4;
        this.dy = (Math.random() - 0.5) * 4;
        this.color = `hsl(${Math.random() * 360}, 100%, 50%)`;
      }
  
      draw() {
        ctxballs.beginPath();
        ctxballs.arc(this.x, this.y, this.radius, 0, Math.PI * 2, false);
        ctxballs.fillStyle = this.color;
        ctxballs.fill();
        ctxballs.closePath();
      }
  
      update() {
        if (this.x + this.radius > canvasballs.width || this.x - this.radius < 0) {
          this.dx = -this.dx;
        }
  
        if (this.y + this.radius > canvasballs.height || this.y - this.radius < 0) {
          this.dy = -this.dy;
        }
  
        this.x += this.dx;
        this.y += this.dy;
  
        this.draw();
      }

    }
      function drawWave(amplitude: number, frequency: number, phase: number, color: string, fillHeight: number) {
        ctxwaves.beginPath();
        ctxwaves.moveTo(0, fillHeight);

        for (let x = 0; x < canvaswaves.width; x++) {
            const y = canvaswaves.height - fillHeight - amplitude * Math.sin((x + phase) * frequency); // Negate y to reverse direction
            ctxwaves.lineTo(x, y);
        }

        ctxwaves.lineTo(canvaswaves.width, 0);
        ctxwaves.lineTo(0, 0);
        ctxwaves.closePath();
        ctxwaves.fillStyle = color;
        ctxwaves.fill();
    }

    let phase = 0;
    let fillHeight = 0;
    let animationspeed = 3;
    function animatewaves() {

      ctxwaves.clearRect(0, 0, canvaswaves.width, canvaswaves.height);
  
      drawWave(50, 0.01, phase, 'rgba(186, 85, 211, 0.6)', fillHeight * 0.97);
      drawWave(50, 0.01, -phase + 20, 'rgba(219, 112, 147, 0.6)', fillHeight * 0.9);
      drawWave(30, 0.01, phase + 50, 'rgba(219, 112, 147, 0.6)', fillHeight * 0.84); 
  
      phase += 1;
      if (fillHeight < canvaswaves.height) {
        fillHeight += animationspeed;
      }
      requestAnimationFrame(animatewaves);
    }
    
  </script>
  
  <canvas bind:this={canvasballs} class="fixed top-0 left-0 w-full h-full z-[-1]"></canvas>
  <canvas bind:this={canvaswaves} class="fixed top-0 left-0 w-full h-full z-1"></canvas>
  
  <style>
    canvas {
      background: #ffe4e1; /* Light pink background */
    }
  </style>

<!-- 
   <script lang="ts">
    export let canvas: HTMLCanvasElement;
    export let wavesFinished: boolean;
    let ctx: CanvasRenderingContext2D;
    let balls: Ball[] = [];

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

    function createBalls() {
        for (let i = 0; i < 7; i++) {
            balls.push(new Ball());
        }
    }

    canvas.addEventListener('drawBalls', (event) => {
        if (!ctx) {
            const customEvent = event as CustomEvent;
            ctx = customEvent.detail;
            createBalls();
        }

        balls.forEach(ball => ball.update());
    });
</script> -->
