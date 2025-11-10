<script lang="ts">
  import { Panel } from "titchy";
  import { CodeXml, Cpu, Database, Frame, HandFist, LibraryBig, Palette, type Icon as IconType } from "@lucide/svelte";

  import { SectionPage } from "$/components";

  type Skill = {
    name: string;
    logo: `/${string}.png`;
    rate: number;
  };

  const languages: Skill[] = [
    { name:"JavaScript", logo:"/imgs/skills/languages/js.png",   rate:5   },
    { name:"TypeScript", logo:"/imgs/skills/languages/ts.png",   rate:5   },
    { name:"HTML5",      logo:"/imgs/skills/languages/html.png", rate:5   },
    { name:"CSS3",       logo:"/imgs/skills/languages/css.png",  rate:5   },
    { name:"C-Sharp",    logo:"/imgs/skills/languages/cs.png",   rate:4   },
    { name:"Python",     logo:"/imgs/skills/languages/py.png",   rate:3.5 },
    { name:"GDScript",   logo:"/imgs/skills/languages/gd.png",   rate:3   },
  ];

  const libraries: Skill[] = [
    { name:"Svelte",     logo:"/imgs/skills/libraries/svelte.png",     rate:5   },
    { name:"React",      logo:"/imgs/skills/libraries/react.png",      rate:5   },
    { name:"Sass",       logo:"/imgs/skills/libraries/sass.png",       rate:5   },
    { name:"Zod",        logo:"/imgs/skills/libraries/zod.png",        rate:5   },
    { name:"Reanimated", logo:"/imgs/skills/libraries/reanimated.png", rate:4   },
    { name:"Express",    logo:"/imgs/skills/libraries/express.png",    rate:3.5 },
    { name:"Solid",      logo:"/imgs/skills/libraries/solid.png",      rate:3   },
  ];

  const frameworks: Skill[] = [
    { name:"SvelteKit", logo:"/imgs/skills/libraries/svelte.png",  rate:5 },
    { name:"NextJS",    logo:"/imgs/skills/frameworks/nextjs.png", rate:5 },
    { name:"Expo",      logo:"/imgs/skills/frameworks/expo.png",   rate:4 },
    { name:".NET",      logo:"/imgs/skills/frameworks/dotnet.png", rate:4 },
  ];

  const technologies: Skill[] = [
    { name:"VS Code",        logo:"/imgs/skills/technologies/vscode.png", rate:3   },
    { name:"Node.js",        logo:"/imgs/skills/technologies/node.png",   rate:5   },
    { name:"Git",            logo:"/imgs/skills/technologies/git.png",    rate:4   },
    { name:"AWS",            logo:"/imgs/skills/technologies/aws.png",    rate:3.5 },
    { name:"WSL",            logo:"/imgs/skills/technologies/wsl.png",    rate:3.5 },
    { name:"GitHub Actions", logo:"/imgs/skills/technologies/github.png", rate:3.5 },
    { name:"Docker",         logo:"/imgs/skills/technologies/docker.png", rate:3   },
    { name:"Godot",          logo:"/imgs/skills/languages/gd.png",        rate:3   },
  ];

  const databases: Skill[] = [
    { name:"Supabase",   logo:"/imgs/skills/databases/supabase.png",   rate:4 },
    { name:"Firebase",   logo:"/imgs/skills/databases/firebase.png",   rate:3 },
    { name:"PostgreSQL", logo:"/imgs/skills/databases/postgresql.png", rate:3 },
    { name:"MySQL",      logo:"/imgs/skills/databases/mysql.png",      rate:3 },
  ];

  const designing: Skill[] = [
    { name:"Figma",       logo:"/imgs/skills/designing/figma.png",       rate:4   },
    { name:"Illustrator", logo:"/imgs/skills/designing/illustrator.png", rate:4   },
    { name:"Photoshop",   logo:"/imgs/skills/designing/photoshop.png",   rate:3.5 },
    { name:"Inline SVG",  logo:"/imgs/skills/designing/svg.png",         rate:3   },
    { name:"FontLab 8",   logo:"/imgs/skills/designing/fontlab.png",     rate:3   },
  ];
</script>

{#snippet group(Icon: typeof IconType, title: string, skillsList: Skill[])}
  <Panel class="group">
    <div class="header">
      <div class="icon">
        <Icon />
      </div>
      {title}
    </div>
    <div class="list">
      {#each skillsList as skill}
        <div class="skill">
          <img
            class="logo"
            src={skill.logo}
            alt="{skill.name}'s logo"
          />
          <span class="name">
            {skill.name}
          </span>
          <span class="rate">
            {skill.rate}/5
          </span>
        </div>
      {/each}
    </div>
  </Panel>
{/snippet}

<SectionPage
  id="skills"
  title="Skills"
  icon={HandFist}
>
  <div class="skills">
    {@render group(CodeXml,    "Languages",    languages   )}
    {@render group(LibraryBig, "Libraries",    libraries   )}
    {@render group(Frame,      "Frameworks",   frameworks  )}
    {@render group(Cpu,        "Technologies", technologies)}
    {@render group(Database,   "Databases",    databases   )}
    {@render group(Palette,    "Designing",    designing   )}
  </div>
</SectionPage>

<style lang="scss">
  @use "@/styles/utils.scss" as *;

  .skills {
    flex-direction: row;
    flex-wrap: wrap;
    gap: 1em;

    :global
    .titchy.panel.group {
      flex: 1;
      padding: 15px;
      border: 2px solid C(accent, 30%);
      background-color: C(accent, 15%);
      border-radius: 15px;

      @include wide-screen { min-width: 30%; }

      &:hover {
        background-color: C(accent, 20%);
        scale: 1.03;
      }

      .header {
        flex-direction: row;
        align-items: center;
        gap: 1ch;

        font-size: 1.15rem;
        font-weight: bold;

        .icon {
          padding: 5px;
          color: C(accent);
          background-color: C(accent, 20%);
          border-radius: 10px;

          :global(svg) { @include size(1.25em); }
        }
      }

      .list {
        flex-direction: row;
        flex-wrap: wrap;
        gap: 1ch;

        .skill {
          flex-direction: row;
          align-items: center;
          gap: 1ch;

          background-color: C(accent, 20%);
          padding: 5px;
          border-radius: 5px;

          &:hover {
            background-color: C(accent, 30%);
            scale: 1.05;
            font-weight: bold;
          }

          .logo {
            @include size(1.2em);
            object-fit: contain;
            border-radius: 5px;
          }

          .rate {
            color: C(accent);
            font-weight: 500;
          }
        }
      }

    }
  }
</style>
