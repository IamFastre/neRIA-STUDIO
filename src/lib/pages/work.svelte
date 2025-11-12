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
    processing: { name:"Processing",   color:"#0465f7", logo:"/imgs/skills/technologies/processing",      },
    tirchy:     { name:"Titchy",       color:"#a8f715", logo:"/imgs/work/titchy/logo.png",                },
  };

  const projects: Project[] = [
    {
      name: "The Winery",
      description: "A Twitter-Reddit hybrid social app, its main goal is to give article-like opinions and rants, with no commenting ability and only a repost one, it allows for more focus on the original post, no commenting ability and rot.",
      date: "Aug 2021",
      logo: "/imgs/work/the-winery/logo.png",
      preview: "/imgs/work/the-winery/logo.png",
      stack: [],
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
