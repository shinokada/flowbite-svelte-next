<script lang="ts">
  import { footerCopyright } from ".";
  import type { FooterCopyrightProps } from "$lib/types";

  let { spanClass, aClass, href, by, copyrightMessage = "All Rights Reserved.", year, ...restProps }: FooterCopyrightProps = $props();

  if (!year) year = new Date().getFullYear();

  const { base, link, bySpan } = $derived(footerCopyright());
</script>

<span class={base({ class: spanClass })}>
  &copy; {year}
  {#if href}
    <a {...restProps} {href} class={link({ class: aClass })}>
      {by}
    </a>
  {:else}
    <span class={bySpan()}>{by}</span>
  {/if}
  {copyrightMessage}
</span>

<!--
@component
[Go to docs](https://flowbite-svelte-next.com/)
## Type
[FooterCopyrightProps](https://github.com/themesberg/flowbite-svelte-next/blob/main/src/lib/types.ts#L605)
## Props
@prop spanClass
@prop aClass
@prop href
@prop by
@prop copyrightMessage = "All Rights Reserved."
@prop year
@prop ...restProps
-->
