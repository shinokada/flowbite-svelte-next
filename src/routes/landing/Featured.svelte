<script lang="ts">
  import Combinator from "../utils/icons/Combinator.svelte";
  import Dev from "../utils/icons/Dev.svelte";
  import Hunt from "../utils/icons/Hunt.svelte";
  import Reddit from "../utils/icons/Reddit.svelte";
  import YouTubeFull from "../utils/icons/YouTubeFull.svelte";
  import Section from "./utils/Section.svelte";

  const features = {
    "#reddit": Reddit,
    "#dev": Dev,
    "#hunt": Hunt,
    "#combinator": Combinator,
    "#youtube": YouTubeFull
  };
</script>

<Section>
  <div class="flex flex-col gap-2">
    <div class="mx-auto mb-4 text-base tracking-tight lg:hidden">Featured in:</div>
    <div class="flex flex-wrap items-center justify-center gap-8 lg:hidden">
      {#each Object.entries(features) as [href, Comp]}
        <Comp />
      {/each}
    </div>
    <div class="hidden flex-wrap items-center justify-center gap-8 self-stretch py-2 lg:flex">
      <div class="text-base tracking-tight">Featured in:</div>
      {#each Object.entries(features) as [href, Comp]}
        <Comp />
      {/each}
    </div>
  </div>
</Section>
