<script lang="ts">
  import dayjs from "dayjs";
  import { fade } from "svelte/transition";
  import { Link, useToaster } from "titchy";
  import { Info } from "@lucide/svelte";

  import { SectionPage } from "$/components";

  const toaster = useToaster();

  const time = dayjs();
  const hour = time.hour();
  const year = time.year();

  const hello =
      hour < 4  ? "Good after midnight"
    : hour < 12 ? "Good morning"
    : hour < 18 ? "Good afternoon"
    : "Good evening";

  let showEasterEgg = $state<boolean>(false);

  // Konami code easter egg.
  $effect(() => {
    let input: string[] = [];
    const konamiCode = ['ArrowUp','ArrowUp','ArrowDown','ArrowDown','ArrowLeft','ArrowRight','ArrowLeft','ArrowRight','KeyB','KeyA'];

    const handler = (e:KeyboardEvent) => {
      input.push(e.code);

      if (input.length > konamiCode.length)
        input.shift();

      if (input.join('-') === konamiCode.join('-')) {
        input = [];
        showEasterEgg =! showEasterEgg;

        toaster.add({
          title: 'Easter Egg',
          content: showEasterEgg ? 'Shown' : 'Hidden',
          type:showEasterEgg ? 'success' : 'info',
          dismissible: true
        });
      }
    };

    window.addEventListener("keydown", handler);
    return () => window.removeEventListener("keydown", handler);
  });

  const sinceYears = (y: number) => {
    const elapsed = year - y;
    const noun    = elapsed > 1 ? "years" : "year";

    return `${elapsed} ${noun}`;
  };
</script>

<SectionPage
  id="about"
  title="About"
  icon={Info}
>
  <p>
    <big>{hello}!</big>
    <br>

    <img
      class="neria-logo"
      src="/imgs/neria/light.png"
      alt="neRIA's logo"
    />
    <span class="name">neRIA STUDIO</span>

    is a one-man team so far, consisting of just me; <strong>Mahmoud al-Kelany</strong>,
    other wise known as <Link href="https://github.com/IamFastre" external>Fastre</Link> as my username.
    I'm currently situated in <strong>Egypt</strong>.
    My main communication languages are <em>English</em> and <em>Arabic</em>.
  </p>

  <p>
    I'm a self-taught <strong>full-stack developer</strong> as well as a <strong>React Native <small>(Expo)</small> developer</strong>.
    <br>
    I have about {sinceYears(2021)} in frontend development and <strong>Node.js</strong> in general,
    and {sinceYears(2022)} in <strong>React</strong> and <strong>React Native</strong>,
    and lastly {sinceYears(2024)} in <strong>Svelte/SvelteKit</strong> and I fell in love with it.
    {#if showEasterEgg}
      <br>
      <span transition:fade={{ delay:350 }}>
        My lawyer (my wife) legally advised me to clarify that I only actually fell in love with my wife, not the framework.
        And that she's my only love in this world.
      </span>
    {/if}
  </p>

  <p>
    I believe clear and precise communication is key, whatever idea you have is doable.
    With good communication between us everything is doable. I'm only here to bring YOUR idea to reality,
    so I also strive to bring it to the best it can be for you and for your use-case.
  </p>

  <p>
    You can check the languages, frameworks, tools and technologies I use/have expertise in in the <Link href="#skills">Skills</Link> section.
    <br>
    I've made a fair share of projects and works that you can check belows on the <Link href="#works">Works</Link> section.
  </p>


  {#if showEasterEgg}
    <p transition:fade={{ delay:350 }}>
      Also! I listen to my mother, and I brush my teeth.
    </p>
  {/if}
</SectionPage>

<style lang="scss">
  @use "@/styles/utils.scss" as *;

  .neria-logo {
    @include size(1.5em);
    vertical-align: middle;
  }

  .name {
    color: C(accent);
    font-weight: bold;
  }
</style>
