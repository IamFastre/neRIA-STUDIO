<script lang="ts">
  import { Dog, Phone } from "@lucide/svelte";

  import { SectionPage } from "$/components";
</script>

<SectionPage
  id="contact"
  title="Contact"
  icon={Phone}
>
  <div class="contact">
    <Dog />
    <span>
      Woof
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
