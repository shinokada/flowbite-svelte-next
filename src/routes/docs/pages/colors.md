---
layout: componentLayout
title: Colors - Flowbite Svelte
breadcrumb_title: Colors - Flowbite Svelte
component_title: Colors
dir: Pages
description: Customize your project and the color of the components from Flowbite Svelte by editing the Tailwind configuration file from the root folder
---

<script>
  import { TableProp, TableDefaultRow, CompoAttributesViewer } from '../../utils';
  import { A, Img, P } from '$lib';
</script>

## Primary color in tailwind.config.cjs

There are 22 colors defined in the <A href="https://github.com/themesberg/flowbite-svelte-next/blob/main/tailwind.config.ts">tailwind.config.ts</A>.

<Img src="/images/colors.webp" alt="Primary colors" class="flex justify-center rounded-lg p-8" />

In the provided code, you can customize the primary and secondary color by modifying the appropriate color values.

```css
@import "tailwindcss";

@plugin 'flowbite/plugin';

@custom-variant dark (&:where(.dark, .dark *));

@theme {
  --color-primary-50: #fff5f2;
  --color-primary-100: #fff1ee;
  --color-primary-200: #ffe4de;
  --color-primary-300: #ffd5cc;
  --color-primary-400: #ffbcad;
  --color-primary-500: #fe795d;
  --color-primary-600: #ef562f;
  --color-primary-700: #eb4f27;
  --color-primary-800: #cc4522;
  --color-primary-900: #a5371b;

  --color-secondary-50: #f0f9ff;
  --color-secondary-100: #e0f2fe;
  --color-secondary-200: #bae6fd;
  --color-secondary-300: #7dd3fc;
  --color-secondary-400: #38bdf8;
  --color-secondary-500: #0ea5e9;
  --color-secondary-600: #0284c7;
  --color-secondary-700: #0369a1;
  --color-secondary-800: #075985;
  --color-secondary-900: #0c4a6e;
}

@source "../node_modules/flowbite-svelte/dist";
@source "../node_modules/flowbite-svelte-icons/dist";
```

## Examples

```svelte example class="flex flex-col gap-4"
<script>
  import { Button, Alert, Card, Navbar, NavBrand, NavLi, NavUl, NavHamburger, Toast } from "flowbite-svelte";
  import { FireOutline } from "flowbite-svelte-icons";
</script>

<Button color="primary">Primary</Button>
<Alert color="primary">Primary</Alert>
<Card href="/cards" color="primary">
  <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-red-800">Noteworthy technology acquisitions 2021</h5>
  <p class="leading-tight font-normal text-gray-700 dark:text-gray-700">Here are the biggest enterprise technology acquisitions of 2021 so far, in reverse chronological order.</p>
</Card>
<Navbar color="primary">
  <NavBrand href="/">
    <img src="/images/flowbite-svelte-icon-logo.svg" class="me-3 h-6 sm:h-9" alt="Flowbite Logo" />
    <span class="self-center text-xl font-semibold whitespace-nowrap dark:text-red-800">Flowbite</span>
  </NavBrand>
  <NavHamburger />
  <NavUl>
    <NavLi href="/" active={true}>Home</NavLi>
    <NavLi href="/about">About</NavLi>
    <NavLi href="/services">Services</NavLi>
    <NavLi href="/pricing">Pricing</NavLi>
    <NavLi href="/contact">Contact</NavLi>
  </NavUl>
</Navbar>
<Toast color="primary">
  {#snippet icon()}
    <FireOutline class="h-6 w-6" />
  {/snippet}
  Dismissable user notification.
</Toast>
```
