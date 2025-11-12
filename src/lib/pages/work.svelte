<script lang="ts">
  import { Boxes, Cat, type Icon as IconType, SatelliteDish, SquareTerminal, Usb } from "@lucide/svelte";

  import { SectionPage } from "$/components";

  type Tech = {
    name:  string;
    color: string;
    logo:  `/${string}.png`;
  };

  type Project = {
    name:        string;
    description: string;
    logo:        `/${string}.png` | typeof IconType;
    preview:     `/${string}.png`;
    date:        `${string} 20${number}`;
    stack:       Tech[];
  };

  const techs: Record<string, Tech> = {
    ts:         { name:"TypeScript",   color:"#3178c6", logo:"/imgs/skills/languages/ts.png"         },
    react:      { name:"React",        color:"#61dbfb", logo:"/imgs/skills/libraries/react.png"      },
    next:       { name:"NextJS",       color:"#000000", logo:"/imgs/skills/frameworks/nextjs.png"    },
    supabase:   { name:"Supabase",     color:"#3ecf8e", logo:"/imgs/skills/databases/supabase.png"   },
    md:         { name:"Markdown",     color:"#54679f", logo:"/imgs/skills/languages/md.png"         },
    rn:         { name:"React Native", color:"#61dbfb", logo:"/imgs/skills/libraries/react.png"      },
    expo:       { name:"Expo",         color:"#000000", logo:"/imgs/skills/frameworks/expo.png"      },
    api:        { name:"External API", color:"#8400ff", logo:SatelliteDish,                          },
    reanimated: { name:"Reanimated",   color:"#b07eff", logo:"/imgs/skills/libraries/reanimated.png" },
    svelte:     { name:"Svelte",       color:"#ff3e00", logo:"/imgs/skills/libraries/svelte.png"      },
    sveltekit:  { name:"SvelteKit",    color:"#ff3e00", logo:"/imgs/skills/libraries/svelte.png"      },
    express:    { name:"Express",      color:"#000000", logo:"/imgs/skills/libraries/express.png"     },
    socketio:   { name:"Socket.IO",    color:"#25c2a0", logo:"/imgs/skills/libraries/socketio.png"    },
    vite:       { name:"Vite",         color:"#ffcb24", logo:"/imgs/skills/technologies/vite.png",    },
    npm:        { name:"npm",          color:"#cb3837", logo:"/imgs/skills/technologies/npm.png",     },
    cs:         { name:"C-Sharp",      color:"#4e29cd", logo:"/imgs/skills/languages/cs.png",         },
    dotnet:     { name:".NET",         color:"#4e29cd", logo:"/imgs/skills/frameworks/dotnet.png",    },
    cli:        { name:"CLI",          color:"#8400ff", logo:SquareTerminal,                          },
    gd:         { name:"GDScript",     color:"#4487b9", logo:"/imgs/skills/languages/gd.png",         },
    godot:      { name:"Godot",        color:"#4487b9", logo:"/imgs/skills/languages/gd.png",         },
    arduino:    { name:"Arduino",      color:"#19999f", logo:"/imgs/work/arduino-radar/logo.png",     },
    serial:     { name:"Serial",       color:"#8400ff", logo:Usb                                      },
    processing: { name:"Processing",   color:"#0465f7", logo:"/imgs/skills/technologies/processing",  },
    tirchy:     { name:"Titchy",       color:"#a8f715", logo:"/imgs/work/titchy/logo.png",            },
  };

  const projects: Project[] = [
    {
      name: "The Winery",
      description: "A Twitter-Reddit hybrid social app, its main goal is to give article-like opinions and rants, with no commenting ability and only a repost one, it allows for more focus on the original post, no commenting ability and rot.",
      date: "Aug 2022",
      logo: "/imgs/work/the-winery/logo.png",
      preview: "/imgs/work/the-winery/logo.png",
      stack: [techs.ts, techs.react, techs.next, techs.supabase, techs.md],
    },
    {
      name: "Tuii",
      description: "A mix-it-all app, mainly made it as a background app but it spiraled into a mixture of minigames and clock faces, with Sudoku, Tic-Tac-Toe and Minesweeper. It was fun and app to build and use.",
      date: "Feb 2024",
      logo: "/imgs/work/tuii/logo.png",
      preview: "/imgs/work/tuii/logo.png",
      stack: [techs.ts, techs.rn, techs.expo, techs.api, tehcs.reanimated],
    },
    {
      name: "Lookset",
      description: "An Iraqi Bingo app built for a client, with admin tools and live data and games. It was a delight to venture into more complex territory making this app for my client, and very happy with it they were.",
      date: "Nov 2024",
      logo: "/imgs/work/lookset/logo.png",
      preview: "/imgs/work/lookset/logo.png",
      stack: [techs.ts, techs.svelte, techs.sveltekit, techs.supabase, techs.express, techs.techs.socketio],
    },
    {
      name: "Titchy",
      description: "A UI component library for Svelte, built on my own for my projects and experience, though you can get it on npm yourself to use, it’s really sleek and versatile, virtually zero-config, though everything is configurable if you wish.",
      date: "Oct 2025",
      logo: "/imgs/work/titchy/logo.png",
      preview: "/imgs/work/titchy/logo.png",
      stacks: [tech.ts, tech.svelte, tech.vite, tech.npm],
    },
    {
      name: "Enuii",
      descirption: "A programming language interpreter for my own custom language named the same; Enuii, built in C# for speed and type strictness. Though it may not be used practically, it was sure great building a custom lexer, parser, semantics analyzer, and evaluator.",
      date: "May 2024",
      logo: "/imgs/work/enuii/logo.png",
      preview: "/imgs/work/enuii/logo.png",
      stacks: [techs.cs, techs.dotnet, techs.cli],
    },
    {
      name: "SuperPong",
      description: "Programming is fun, but games are more fun, game dev? is not fun. Though I must admit I do love the simplicity yet challenge of this project, a game made in Godot. It’s Pong but with super abilities and local multiplayer and a CPU mode.",
      date: "Sep 2024",
      logo: "/imgs/work/superpong/logo.png",
      preview: "/imgs/work/superpong/logo.png",
      stacks: [techs.gd, techs.godot],
    },
    {
      name: "Arduino Sonar",
      description: "Boredom can get you places, these places may be so far from home. While I am no Arduino expert, I built a double sensor Sonar for Arduino for the help of a friend. Complete with a Processing GUI over Serial Bus.",
      date: "Nov 2024",
      logo: "/imgs/work/arduino-sonar/logo.png",
      preview: "/imgs/work/arduino-sonar/logo.png",
      stacks: [techs.arduino, techs.serial, techs.processing],
    },
    {
      name: "Portfolio",
      description: "This very website you’re on right now, while I’m not sure if it should be added here, I must say I’m proud of it, every line of code in it is written by me, no templates, no external help. Surely a delight to see your achievements on a platform that’s also your own.",
      date: "Nov 2025",
      logo: "/imgs/work/portfolio/logo.png",
      preview: "/imgs/work/portfolio/logo.png",
      stacks: [techs.ts, techs.svelte, techs.sveltekit, techs.titchy],
    },
  ];
</script>

<SectionPage
  id="work"
  title="Work"
  icon={Boxes}
>
  <div class="work">
    <Cat />
    <span>
      Meow
    </span>
  </div>
</SectionPage>

<style lang="scss">
  @use "@/styles/utils.scss" as *;

  .work {
    flex: 1;
    align-items: center;
    justify-content: center;
  }
</style>
