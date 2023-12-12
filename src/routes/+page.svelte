<script lang="ts">
  // Imports
  import gsap from 'gsap'
  // Props

  // Constant Variables
  const centerX = window.innerWidth / 2
  const centerY = window.innerHeight / 2

  // State Variables
  let m = { x: 0, y: 0 };
  let card: HTMLElement;

  // Event Handlers
  const handleMove = (event: PointerEvent) => {
    m.x = event.clientX
    m.y = event.clientY


    // Get offset of pointer from center
    const offsetX = ((m.x - centerX) / centerX) * 30
    const offsetY = ((m.y - centerY) / centerY) * 30

    gsap.to(card, {rotateX: -1 * offsetY, rotateY: offsetX})
  }
  // Lifecycle Functions

  // Reactive Statements

</script>



<main on:pointermove={handleMove} class="h-full w-full grid place-items-center">
  <article bind:this={card} class="h-96 w-80 bg-gradient-to-tr from-cyan-500 to-fuchsia-500 rounded-2xl shadow-lg relative">
    <div id="shadow" class="bg-gray-900 absolute inset-3 rounded-2xl blur-xl"></div>
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