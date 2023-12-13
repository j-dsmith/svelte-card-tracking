<script lang="ts">
  // Imports
  import gsap from 'gsap'
  // Props

  // Constant Variables

  // State Variables
  const mouseCoords = { x: 0, y: 0 };
  let card: HTMLElement;

  let innerWidth: number;
  let innerHeight: number;
  let centerX: number;
  let centerY: number;

  // Event Handlers
  const handleMove = (event: PointerEvent) => {
    mouseCoords.x = event.clientX
    mouseCoords.y = event.clientY


    // Get offset of pointer from center
    const offsetX = ((mouseCoords.x - centerX) / centerX) * 30
    const offsetY = ((mouseCoords.y - centerY) / centerY) * 30

    gsap.to(card, {rotateX: -1 * offsetY, rotateY: offsetX})
  }
  // Lifecycle Functions

  // Reactive Statements
  $: {
    centerX = innerWidth / 2
    centerY = innerHeight / 2
  }

</script>

<svelte:window bind:innerHeight={innerHeight} bind:innerWidth={innerWidth} />

<main on:pointermove={handleMove} class="h-full w-full grid place-items-center">
  <article bind:this={card} class="h-96 w-80 bg-gradient-to-tr from-cyan-500 to-fuchsia-500 rounded-2xl shadow-lg relative">
    <div id="shadow" class="bg-gray-900 absolute inset-3 rounded-md blur-xl"></div>
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
    transform: translateZ(50px);
  }

  #shadow {
    transform: translateZ(1px)
  }
</style>