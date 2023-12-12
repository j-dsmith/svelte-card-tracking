<script lang="ts">
  // Imports
  import gsap from 'gsap'
  // Props

  // Constant Variables

  // State Variables
  let card: HTMLElement;

  // Event Handlers

  // Lifecycle Functions

  // Reactive Statements
</script>



<main class="h-full w-full grid place-items-center">
  <article bind:this={card} class="h-96 w-80 bg-gradient-to-tr from-cyan-500 to-fuchsia-500 rounded-2xl shadow-lg relative">
    <div class="bg-gray-800 absolute inset-3 rounded-2xl blur-lg"></div>
    <div class="bg-gray-900 absolute inset-4 rounded-2xl"></div>
  </article>
</main>

<style lang="postcss">
  article {
    transform-style: preserve-3d;
    transform: perspective(5000px);
  }

  div {
    transform-style: preserve-3d;
    transform: translateZ(100px);
  }
</style>