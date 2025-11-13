<script lang="ts">
  import { Cat, Phone } from "@lucide/svelte";

  import { SectionPage } from "$/components";
</script>

<SectionPage
  id="contact"
  title="Contact"
  icon={Phone}
>
  <div class="contact">
    <Cat />
    <span>
      Meow
    </span>
  </div>
</SectionPage>

<style lang="scss">
  @use "@/styles/utils.scss" as *;

  .contact {
    flex: 1;
    align-items: center;
    justify-content: center;
  }
</style>
