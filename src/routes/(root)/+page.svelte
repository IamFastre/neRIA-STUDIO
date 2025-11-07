<main data-variant="page-nav">
  <div class="hello">
    <span>Hi, World!</span>
    <span>How's it going?</span>
  </div>
</main>

<style lang="scss">
  @use "@/styles/utils.scss" as *;

  .hello {
    flex: 1;
    align-items: center;
    justify-content: center;

    span {
      text-align: center;
      font-size: 6rem;
      font-weight: 100;
    }
  }
</style>
