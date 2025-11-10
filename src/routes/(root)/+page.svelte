<script lang="ts">
  import { untrack } from "svelte";
  import { fade, fly } from "svelte/transition";
  import { page } from "$app/state";
  import { goto } from "$app/navigation";
  import { Button } from "titchy";
  import { ChevronDown } from "@lucide/svelte";

  import { Gem } from "$/svgs";
  import { AboutPage, ContactPage, SkillsPage, WorkPage } from "$/pages";

  let contentShown = $state(!!page.url.hash);

  const onClickGem = () => {
    contentShown =! contentShown;
  };

  $effect(() => {
    untrack(() => {
      goto(page.url.hash);
    });
  });
</script>

<main class="landing-page" data-variant="page-nav">
  <div class="container" class:content-shown={contentShown}>
    <div class="gem">
      <Button
        variant="wrapper"
        scaling={false}
        onclick={onClickGem}
      >
        <Gem />
      </Button>
    </div>
    {#if contentShown}
      <div class="content" in:fly={{ x:"-200px", delay:250, opacity:0 }}>
        <h1>Hello!</h1>
        <span>
          Welcome to the <strong>neRIA STUDIO</strong> showcase.
        </span>
      </div>
    {/if}
  </div>
  {#if contentShown}
    <div class="scroll-down" transition:fade={{ duration:200 }}>
      <ChevronDown />
      <span>Scroll down</span>
    </div>
  {/if}
</main>

{#if contentShown}
  <AboutPage />
  <SkillsPage />
  <WorkPage />
  <ContactPage />
{/if}

<style lang="scss">
  @use "@/styles/utils.scss" as *;

  $gem-size: min(35dvw, 25dvh);

  .landing-page {
    align-items: center;
    justify-content: center;
    padding: 10%;

    .container {
      @include size($gem-size);
      align-items: center;
      gap: 10%;

      transition-timing-function: ease;
      transition-duration: 250ms;

      &.content-shown {
        @include size(100%);
        :global svg {
          filter: drop-shadow(0 0 25px C(accent, 60%));

          #gem #gem-glint {
            animation-play-state: running;
          }
        }
      }

      .content {
        align-items: start;
        transform-origin: left;

        h1 {
          font-size: 5rem;
          font-weight: 300;
        }

        span {
          font-weight: 200;
          margin-inline-start: 0.5em;
        }
      }
    }

    .gem {
      @include size(calc($gem-size + 30px), 'all');
      align-items: center;
      justify-content: center;
      z-index: 1;

      :global
      .titchy.button {
        @include size($gem-size);
        rotate: -45deg;
      }
    }

    .scroll-down {
      flex-direction: row;
      align-items: center;
      gap: 1ch;
      position: absolute;
      bottom: 5%;

      :global(svg) {
        animation: blink 1s ease-in-out infinite;
      }
    }
  }

  @keyframes blink {
    0%   { opacity: 0; }
    40%  { opacity: 1; }
    60%  { opacity: 1; }
    100% { opacity: 0; }
  }

  @include small-screen {
    .landing-page {
      .container {
        flex-direction: column;

        .content {
          align-items: center;
          text-align: center;
        }
      }
    }
  }

  @include wide-screen {
    .landing-page {
      .container {
        flex-direction: row;

        .content {
          align-items: start;
          text-align: start;
        }
      }
    }
  }
</style>
