<script lang="ts">
  import { Boxes, Cat } from "@lucide/svelte";

  import { SectionPage } from "$/components";
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
