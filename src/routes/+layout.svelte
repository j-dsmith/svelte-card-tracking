<script>
  import '../app.css'
</script>

<slot/>

<style lang="postcss">
  :global(body, html) {
    height: 100%;
    background-color: theme(colors.gray.950);
  }
</style>