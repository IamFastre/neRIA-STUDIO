<script lang="ts">
  import { Boxes, Cat, GitFork, type Icon as IconType, Link as LinkIcon, SatelliteDish, SquareTerminal, Usb } from "@lucide/svelte";

  import { SectionPage } from "$/components";
  import { Carousel, Link, Panel } from "titchy";

  type Tech = {
    name:  string;
    color: string;
    logo:  `/${string}.png` | typeof IconType;
  };

  type Project = {
    name:        string;
    description: string;
    logo:        `/${string}.png`;
    preview:     `/${string}.png`;
    site?:       `https://${string}`;
    repo?:       `https://github.com/${string}/${string}`;
    date:        `${string} 20${number}`;
    stack:       Tech[];
  };

  const tech: Record<string, Tech> = {
    ts:         { name:"TypeScript",   color:"#3178c6", logo:"/imgs/skills/languages/ts.png"             },
    react:      { name:"React",        color:"#61dbfb", logo:"/imgs/skills/libraries/react.png"          },
    next:       { name:"NextJS",       color:"#ffffff", logo:"/imgs/skills/frameworks/nextjs.png"        },
    supabase:   { name:"Supabase",     color:"#3ecf8e", logo:"/imgs/skills/databases/supabase.png"       },
    md:         { name:"Markdown",     color:"#54679f", logo:"/imgs/skills/languages/md.png"             },
    rn:         { name:"React Native", color:"#61dbfb", logo:"/imgs/skills/libraries/react.png"          },
    expo:       { name:"Expo",         color:"#ffffff", logo:"/imgs/skills/frameworks/expo.png"          },
    reanimated: { name:"Reanimated",   color:"#b07eff", logo:"/imgs/skills/libraries/reanimated.png"     },
    svelte:     { name:"Svelte",       color:"#ff3e00", logo:"/imgs/skills/libraries/svelte.png"         },
    sveltekit:  { name:"SvelteKit",    color:"#ff3e00", logo:"/imgs/skills/libraries/svelte.png"         },
    express:    { name:"Express",      color:"#ffffff", logo:"/imgs/skills/libraries/express.png"        },
    socketio:   { name:"Socket.IO",    color:"#25c2a0", logo:"/imgs/skills/libraries/socketio.png"       },
    vite:       { name:"Vite",         color:"#ffcb24", logo:"/imgs/skills/technologies/vite.png",       },
    npm:        { name:"npm",          color:"#cb3837", logo:"/imgs/skills/technologies/npm.png",        },
    cs:         { name:"C-Sharp",      color:"#4e29cd", logo:"/imgs/skills/languages/cs.png",            },
    dotnet:     { name:".NET",         color:"#4e29cd", logo:"/imgs/skills/frameworks/dotnet.png",       },
    gd:         { name:"GDScript",     color:"#4487b9", logo:"/imgs/skills/languages/gd.png",            },
    godot:      { name:"Godot",        color:"#4487b9", logo:"/imgs/skills/languages/gd.png",            },
    arduino:    { name:"Arduino",      color:"#19999f", logo:"/imgs/work/arduino-sonar/logo.png",        },
    processing: { name:"Processing",   color:"#0465f7", logo:"/imgs/skills/technologies/processing.png", },
    titchy:     { name:"Titchy",       color:"#a8f715", logo:"/imgs/work/titchy/logo.png",               },
    api:        { name:"External API", color:"#8400ff", logo:SatelliteDish,                              },
    cli:        { name:"CLI",          color:"#8400ff", logo:SquareTerminal,                             },
    serial:     { name:"Serial",       color:"#8400ff", logo:Usb                                         },
  };

  const projects: Project[] = [
    {
      name: "The Winery",
      description: "A Twitter-Reddit hybrid social app, its main goal is to give article-like opinions and rants, with no commenting ability and only a repost one, it allows for more focus on the original post, no commenting ability and rot.",
      date: "Aug 2022",
      logo: "/imgs/work/the-winery/logo.png",
      preview: "/imgs/work/the-winery/preview.png",
      site: "https://winery.neria.studio",
      repo: "https://github.com/IamFastre/The-Winery",
      stack: [tech.ts, tech.react, tech.next, tech.supabase, tech.md],
    },
    {
      name: "Tuii",
      description: "A mix-it-all app, mainly made it as a background app but it spiraled into a mixture of mini-games and clock faces, with Sudoku, Tic-Tac-Toe and Minesweeper. It was fun and app to build and use.",
      date: "Feb 2024",
      logo: "/imgs/work/tuii/logo.png",
      preview: "/imgs/work/tuii/preview.png",
      repo: "https://github.com/IamFastre/Tuii",
      stack: [tech.ts, tech.rn, tech.expo, tech.api, tech.reanimated],
    },
    {
      name: "Lookset",
      description: "An Iraqi Bingo app built for a client, with admin tools and live data and games. It was a delight to venture into more complex territory making this app for my client, and very happy with it they were.",
      date: "Nov 2024",
      logo: "/imgs/work/lookset/logo.png",
      preview: "/imgs/work/lookset/preview.png",
      site: "https://lookseet.com",
      stack: [tech.ts, tech.svelte, tech.sveltekit, tech.supabase, tech.express, tech.socketio],
    },
    {
      name: "Titchy",
      description: "A UI component library for Svelte, built on my own for my projects and experience, though you can get it on npm yourself to use, it’s really sleek and versatile, virtually zero-config, though everything is configurable if you wish. It's the very UI you see in the website here.",
      date: "Oct 2025",
      logo: "/imgs/work/titchy/logo.png",
      preview: "/imgs/work/titchy/preview.png",
      site: "https://titchy.neria.studio",
      repo: "https://github.com/neRIA-Studio/Titchy",
      stack: [tech.ts, tech.svelte, tech.vite, tech.npm],
    },
    {
      name: "Fussr",
      description: "A Q&A website without hassle for everyone with extra focus on MENA devs and tech savvies. Originally made for the Qimma hackathon, it still is open for all.",
      date: "Nov 2025",
      logo: "/imgs/work/fussr/logo.png",
      preview: "/imgs/work/fussr/preview.png",
      site: "https://fussr.neria.studio",
      repo: "https://github.com/IamFastre/Fussr",
      stack: [tech.ts, tech.svelte, tech.sveltekit, tech.supabase, tech.md],
    },
    {
      name: "Enuii",
      description: "A programming language interpreter for my own custom language named the same; Enuii, built in C# for speed and type strictness. Though it may not be used practically, it was sure great building a custom lexer, parser, semantics analyzer, and evaluator.",
      date: "May 2024",
      logo: "/imgs/skills/languages/cs.png",
      preview: "/imgs/work/enuii/preview.png",
      repo: "https://github.com/IamFastre/Enuii",
      stack: [tech.cs, tech.dotnet, tech.cli],
    },
    {
      name: "SuperPong",
      description: "Programming is fun, but games are more fun, game dev? is not fun. Though I must admit I do love the simplicity yet challenge of this project, a game made in Godot. It’s Pong but with super abilities and local multiplayer and a CPU mode.",
      date: "Sep 2024",
      logo: "/imgs/work/superpong/logo.png",
      preview: "/imgs/work/superpong/preview.png",
      site: "https://iamfastre.github.io/super-pong/",
      repo: "https://github.com/IamFastre/super-pong",
      stack: [tech.gd, tech.godot],
    },
    {
      name: "Arduino Sonar",
      description: "Boredom can get you places, these places may be so far from home. While I am no Arduino expert, I built a double sensor Sonar for Arduino for the help of a friend. Complete with a Processing GUI over Serial Bus.",
      date: "Nov 2024",
      logo: "/imgs/work/arduino-sonar/logo.png",
      preview: "/imgs/work/arduino-sonar/preview.png",
      repo: "https://github.com/IamFastre/arduino-sonar",
      stack: [tech.arduino, tech.serial, tech.processing],
    },
    {
      name: "Portfolio",
      description: "This very website you’re on right now, while I’m not sure if it should be added here, I must say I’m proud of it, every line of code in it is written by me, no templates, no external help. Surely a delight to see your achievements on a platform that’s also your own.",
      date: "Nov 2025",
      logo: "/imgs/work/portfolio/logo.png",
      preview: "/imgs/work/portfolio/preview.png",
      site: "https://neria.studio",
      repo: "https://github.com/IamFastre/neRIA-STUDIO",
      stack: [tech.ts, tech.svelte, tech.sveltekit, tech.titchy],
    },
  ];
</script>

<SectionPage
  id="work"
  title="Work"
  icon={Boxes}
>
  <div class="work">
    <p>
      These are some of my recent projects that I hope give you an idea of me and my way of work.
    </p>
    <Carousel class="projects">
      {#each projects as proj, i (i)}
        <Panel variant="secondary" class="project">
          <div class="preview" style="--preview: url({proj.preview})">
          </div>
          <div class="info">
            <div class="logo">
              <img
                src={proj.logo}
                alt="{proj.name}'s logo"
              />
              <div class="date">
                {proj.date}
              </div>
            </div>
            <div class="body">
              <span class="name">
                {proj.name}
              </span>
              <span class="description">
                {proj.description}
              </span>
              {#if proj.site || proj.repo}
                <div class="links">
                  {#if proj.site}
                    <div class="site">
                      <LinkIcon />
                      <Link class="site" href={proj.site} external>
                        {new URL(proj.site).host}
                      </Link>
                    </div>
                  {/if}
                  {#if proj.repo}
                    <div class="repo">
                      <GitFork />
                      <Link class="repo" href={proj.repo} external>
                        {new URL(proj.repo).pathname.replace(/^\//, "")}
                      </Link>
                    </div>
                  {/if}
                </div>
              {/if}
              <div class="stack">
                {#each proj.stack as tech}
                  <div class="tech" style="--color: {tech.color}">
                    {#if typeof tech.logo === 'string'}
                      <img
                        src={tech.logo}
                        alt="{tech.name}'s logo"
                        class="icon"
                      />
                    {:else}
                      {@const Icon = tech.logo}
                      <Icon class="icon" />
                    {/if}
                    <span class="name">
                      {tech.name}
                    </span>
                  </div>
                {/each}
              </div>
            </div>
          </div>
        </Panel>
      {/each}
    </Carousel>
  </div>
</SectionPage>
<style lang="scss">
  @use "@/styles/utils.scss" as *;

  .work {
    flex: 1;
    gap: 1em;

    :global
    .titchy.carousel.projects {
      --carousel-content-width: 70dvw;
      align-self: center;

      .project {
        $g: 10px;
        padding: 0;
        justify-content: end;
        height: 500px;
        overflow: hidden;

        .preview {
          @include fill-absolute();
          background-image: var(--preview);
          background-size: 100%;
          background-position: top;
          background-repeat: repeat;
        }

        .info {
          flex-direction: row;
          gap: $g;
          padding: $g;
          border-radius: 10px;
          background-color: C(accent, 10%);
          backdrop-filter: blur(35px);

          .logo {
            align-items: center;
            justify-content: space-between;
            gap: $g;

            img {
              @include size(4rem);
              object-fit: contain;
              // background-color: C(accent, 20%);
              // border: 1px solid C(accent);
              // border-radius: 10px;
            }

            .date {
              font-size: 0.6rem;
              color: C(secondary, 30%);
            }
          }

          .body {
            align-items: start;
            justify-content: center;
            gap: calc($g / 2);

            > .name {
              color: C(accent);
              font-size: 1.1rem;
              font-weight: bold;
            }

            > .description {
              color: C(secondary, 75%);
              font-size: 0.85rem;
            }

            > .links {
              gap: calc($g / 2);
              font-size: 0.9rem;

              > * {
                flex-direction: row;
                align-items: center;
                gap: 1ch;

                :global
                .titchy.link:is(.site, .repo) {
                  --link-accent-color: #{C(secondary)};
                }

                :global(svg) {
                  color: C(accent);
                  @include size(1em);
                }
              }
            }

            > .stack {
              flex-direction: row;
              flex-wrap: wrap;
              gap: $g;
              margin-top: $g;

              > .tech {
                flex-direction: row;
                align-items: center;

                background-color: set-alpha(var(--color), 15%);
                color: var(--color);

                padding: calc($g / 2);
                border-radius: calc($g / 2);

                font-size: 0.75rem;
                font-weight: bold;
                gap: calc($g / 2);

                .icon {
                  @include size(1.2em, 'all');
                  object-fit: contain;
                }
              }
            }
          }
        }
      }
    }
  }
</style>
