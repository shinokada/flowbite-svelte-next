<script lang="ts">
  import clsx from "clsx";
  import { sitebarbrand } from ".";
  import type { SidebarBrandProps } from "$lib/types";

  let { children, site, imgClass, spanClass, class: className, ...restProps }: SidebarBrandProps = $props();

  const { base, img, span } = $derived(sitebarbrand());
</script>

<a {...restProps} href={site?.href ? site.href : "/"} class={base({ class: clsx(className) })}>
  {#if site}
    <img src={site.img} class={img({ class: imgClass })} alt={site.name} />
    <span class={span({ class: spanClass })}>{site.name}</span>
  {:else if children}
    {@render children()}
  {/if}
</a>

<!--
@component
[Go to docs](https://flowbite-svelte-next.com/)
## Type
[SidebarBrandProps](https://github.com/themesberg/flowbite-svelte-next/blob/main/src/lib/types.ts#L1159)
## Props
@prop children
@prop site
@prop imgClass
@prop spanClass
@prop class: className
@prop ...restProps
-->
