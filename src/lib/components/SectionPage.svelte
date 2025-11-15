<script lang="ts">
  import type { Snippet } from "svelte";
  import type { Icon as IconType } from "@lucide/svelte";

  import { WavePage } from "$/components";

  interface Props {
    id: string;
    title: string;
    icon: typeof IconType;
    children: Snippet;
  }

  const {
    id,
    title,
    icon: Icon,
    children,
  }: Props = $props();
</script>

<WavePage {id} data-expanding>
  <header>
    <Icon />
    <span>{title}</span>
  </header>

  {@render children()}
</WavePage>

<style lang="scss">
  @use "@/styles/utils.scss" as *;

  :global .wave-page {
    .content-container {
      flex: 1;
      gap: 20px;
    }
  }

  header {
    flex-direction: row;
    align-items: center;
    gap: 0.35em;
    font-size: 3rem;

    span {
      color: C(accent);
      font-weight: 600;
    }

    :global(svg) {
      @include size(1em);
      opacity: 0.35;
    }
  }

  :global(p, .padded) {
    @include wide-screen {
      padding: 0 70px;
    }
  }
</style>
