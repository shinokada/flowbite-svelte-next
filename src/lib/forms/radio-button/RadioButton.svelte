<script lang="ts" generics="T">
  import Button from "$lib/buttons/Button.svelte";
  import clsx from "clsx";
  import { radioButton } from ".";
  import type { RadioButtonProps } from "$lib/types";

  let { children, group = $bindable<T>(), value = $bindable<T>(), inline, pill, outline, size, color, shadow, class: className, ...restProps }: RadioButtonProps<T> = $props();

  let base = $derived(radioButton({ inline, checked: value == group, class: clsx(className) }));
</script>

<Button tag="label" checked={value === group} {pill} {outline} {size} {color} {shadow} class={base}>
  <input type="radio" bind:group {value} {...restProps} class="sr-only" />
  {@render children?.()}
</Button>

<!--
@component
[Go to docs](https://flowbite-svelte-next.com/)
## Props
@props: 
-->
