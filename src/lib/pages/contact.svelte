<script lang="ts">
  import type { Component } from "svelte";
  import { Button, Input, InputWrapper, Link, Panel, Textarea } from "titchy";
  import { Box, Github, type Icon as IconType, Mail, Phone, Send, TextCursorInput, TextInitial, Trash2 } from "@lucide/svelte";

  import { SectionPage } from "$/components";
  import { Discord, Instagram, Threads } from "$/svgs";

  type Field = {
    name:     string;
    link:     string;
    icon:     typeof IconType | Component;
    display?: string;
  };

  const fields: Field[] = [
    { name:"Email",     link:"mailto:contact@neria.studio",              icon:Mail                                  },
    { name:"GitHub",    link:"https://github.com/neRIA-Studio",          icon:Github,       display:"@neRIA-Studio" },
    { name:"GitHub",    link:"https://github.com/IamFastre",             icon:Github,       display:"@IamFastre"    },
    { name:"Instagram", link:"https://www.instagram.com/studio.neRIA",   icon:Instagram,    display:"@studio.neRIA" },
    { name:"Threads",   link:"https://www.threads.com/@studio.neRIA",     icon:Threads,      display:"@studio.neRIA" },
    { name:"Discord",   link:"@neria_0x57",                              icon:Discord,      display:"@neria_0x57"   },
    { name:"Minecraft", link:"https://namemc.com/profile/TheRealFastre", icon:Box,          display:"TheRealFastre" },
  ];

  let subject = $state<string>("");
  let body    = $state<string>("");

  const sendHref = $derived.by(() => {
    if (!subject || !body)
      return;

    const url = new URL("mailto:contact@neria.studio");

    url.searchParams.set('subject', subject);
    url.searchParams.set('body', body);

    return url.toString();
  });

  const discardMail = () => {
    if (subject) subject = "";
    if (body)    body    = "";
  };
</script>

<SectionPage
  id="contact"
  title="Contact"
  icon={Phone}
>
  <div class="contact">
    <div class="fields">
      {#each fields as field}
        {@const Icon = field.icon}
        <Link
          href={URL.canParse(field.link) ? field.link : undefined}
          class="field"
          variant="wrapper"
          external
        >
          <div class="platform">
            <Icon />
            {field.name}
          </div>
          <div class="link">
            {#if URL.canParse(field.link)}
              <!-- I love you, RegEx -->
              <Link>{field.display ?? field.link.replace(/^.+:(\/+)?/, '')}</Link>
            {:else}
              {field.display ?? field.link}
            {/if}
          </div>
        </Link>
      {/each}
    </div>
    <div class="email">
      <div class="title">
        <span>E</span>
        <span>M</span>
        <span>A</span>
        <span>I</span>
        <span>L</span>
        <span> </span>
        <Mail />
        <span> </span>
        <span>M</span>
        <span>E</span>
      </div>
      <Panel class="email-box">
        <InputWrapper
          icon={TextCursorInput}
          label="Subject"
          side-actions={{ clearable:'always' }}
        >
          <Input bind:value={subject} type="text" placeholder="Your email subject." />
        </InputWrapper>
        <InputWrapper
          icon={TextInitial}
          label="Body"
          side-actions={{ pastable:'hover', clearable:'always' }}
        >
          <Textarea bind:value={body} placeholder="Body of your email."  />
        </InputWrapper>
        <div class="actions">
          <Link class="send" href={sendHref} variant="wrapper" external>
            <Button scaling={false} disabled={!sendHref} onclick={() => setTimeout(discardMail, 10)}>
              <Send />
              Send
            </Button>
          </Link>
          <Button scaling={false} disabled={!subject && !body} onclick={discardMail}>
            <Trash2 />
          </Button>
        </div>
      </Panel>
    </div>
  </div>
</SectionPage>

<style lang="scss">
  @use "@/styles/utils.scss" as *;

  .contact {
    flex: 1;
    gap: 2em;

    @include wide-screen {
      flex-direction: row;
      justify-content: space-between;
    }

    .fields {
      align-items: stretch;
      gap: 1em;

      :global
      .titchy.link.field {
        flex-direction: row;
        align-items: center;
        gap: 0.75em;
        padding: 1em;
        border-radius: 1em;
        background-color: C(accent, 10%);

        &:hover {
          scale: 1.025;

          .platform :global(svg) { scale: 1.15; }
          &:nth-child(2n)     { .platform :global(svg) { rotate: -15deg; } }
          &:nth-child(2n - 1) { .platform :global(svg) { rotate:  15deg; } }
        }

        .platform {
          flex-direction: row;
          align-items: center;
          gap: 0.75em;
          font-weight: 500;

          :global(svg) {
            color: C(accent);
            @include size(1.75em);
          }
        }

        .link {
          --link-accent-color: #{C(secondary)};
        }
      }
    }

    .email {
      flex: 1;
      gap: 7.5px;

      .title {
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        padding: 0 1ch;
        color: C(accent);

        :global(svg) {
          @include size(1.33em);
          stroke-width: 1px;
        }
      }

      :global
      .titchy.panel.email-box {
        flex: 1;
        padding: 7.5px;

        .titchy.input-wrapper:nth-of-type(2) {
          flex: 1;
          textarea {
            resize: none;
            @include height(100%, 'all');
            min-height: 200px;
          }
        }

        > .actions {
          flex-direction: row;
          gap: 10px;
          .send { flex: 1; }
        }
      }
    }
  }
</style>
