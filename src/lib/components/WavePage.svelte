<script lang="ts">
  import type { HTMLAttributes } from "svelte/elements";
  import { SineWave } from "$/svgs";

  const props: HTMLAttributes<HTMLElement> = $props();
</script>

<main
  {...props}
  data-variant={props['data-variant'] ?? "page-nav"}
  class={["wave-page", props.class]}
>
  <div class="wave-container">
    <div class="buffer"></div>
    <SineWave />
  </div>
  <div class="content-container">
    {@render props.children?.()}
  </div>
</main>

<style lang="scss">
  @use "@/styles/utils.scss" as *;

  .wave-page {
    background-color: var(--bg-color);

    &:nth-child(2n) {
      --wave-color: #{C(primary)};
      --bg-color: #{C(tertiary, 15%)};
    }

    &:nth-child(2n+1) {
      --wave-color: #{C(tertiary, 15%)};
      --bg-color: #{C(primary)};
    }

    .wave-container {
      $buffer: 25px;

      width: 100%;
        overflow: hidden;

      :global(.wave) {
        width: 200%;
        fill: var(--wave-color);
      }

      .buffer {
        background-color: var(--wave-color);
        height: $buffer;
        width: 100%;
      }
    }
  }

  @include small-screen {
    .content-container {
      padding: 10px 20px;
    }

    .wave-page:last-of-type {
      .content-container {
        padding-bottom: 20px;
      }
    }
  }

  @include wide-screen {
    .content-container {
      padding: 50px;
    }
  }
</style>