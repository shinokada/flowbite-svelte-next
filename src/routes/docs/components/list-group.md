---
layout: componentLayout
title: Svelte List Group - Flowbite
breadcrumb_title: Svelte List Group
component_title: List Group
dir: Components
description: Use the list group component to display a series of items, buttons or links inside a single element
thumnailSize: w-36
---

<script>
  import { CompoAttributesViewer,  GitHubCompoLinks, toKebabCase } from '../../utils'
  import { Badge, Heading, P, A } from '$lib'
  const dirName = toKebabCase(component_title)
</script>

The list group component can be used to display a series of elements, buttons or links inside a single card component similar to a sidebar.

## Setup

```svelte example hideOutput
<script>
  import { Listgroup, ListgroupItem } from "flowbite-svelte";
</script>
```

## Default list group

Here’s an example of a list group that you can use right away.

```svelte example class="flex justify-center" hideResponsiveButtons
<script>
  import { Listgroup } from "flowbite-svelte";
  let simpleList = ["Profile", "Settings", "Messages", "Download"];
</script>

<Listgroup items={simpleList} class="w-48" />
```

## List group with links

You can also display a series of links inside the list group element. Notice how items provide the `href` field.

You need to set the list to `active` mode to enable hovering, focus and links.

If list is active and data items contain `href` field entries are presented as `<a>` elements.

You can pass extra properties to the `<a>` element by setting the `attrs` atrribute in the items list.

```svelte example class="flex justify-center"
<script>
  import { Listgroup } from "flowbite-svelte";
  let links = [
    { name: "Accordions", href: "/docs/components/accordion", current: true },
    { name: "Alerts", href: "/docs/components/alert" },
    { name: "Badges", href: "/docs/components/badge" },
    { name: "Breadcrumbs", href: "/docs/components/breadcrumb", attrs: { target: "_blank" } }
  ];
</script>

<Listgroup active items={links} class="w-48" />
```

## List group with buttons

It is also possible to display a list of button element inside the list group component. The following example includes an active and disabled item as well.

You need to set the list to `active` mode to enable hovering, focus and `onclick`.

If list is active and data items do not contain `href` field entries are presented as `<button>` elements triggering `onclick` events.

You can pass extra properties to the `<button>` element by setting the `attrs` atrribute in the items list.

```svelte example class="flex justify-center" hideResponsiveButtons
<script>
  import { Listgroup, ListgroupItem } from "flowbite-svelte";
  let buttons = [
    { name: "Profile", mycustomfield: "data1", current: true },
    { name: "Settings", mycustomfield: "data2" },
    { name: "Messages", mycustomfield: "data3" },
    { name: "Download", mycustomfield: "data4", disabled: true, attrs: { type: "submit" } }
  ];
</script>

<Listgroup active items={buttons} class="w-48" onclick={(e) => alert(Object.entries(e?.detail ?? {}))} />
```

## List group with icons

Use the following example to create a list of buttons as a menu together with SVG icons.

```svelte example class="flex justify-center" hideResponsiveButtons
<script>
  import { Listgroup } from "flowbite-svelte";
  import { AdjustmentsHorizontalSolid, DownloadSolid, MessagesSolid, UserCircleSolid } from "flowbite-svelte-icons";
  let icons = [
    { name: "Profile", Icon: UserCircleSolid },
    { name: "Settings", Icon: AdjustmentsHorizontalSolid },
    { name: "Messages", Icon: MessagesSolid },
    { name: "Download", Icon: DownloadSolid }
  ];
</script>

<Listgroup active items={icons} class="w-48" onclick={console.log} />
```

## Horizontal list group

Use the `horizontal` property to change the direction of list items.

```svelte example class="flex justify-center" hideResponsiveButtons
<script>
  import { Listgroup, ListgroupItem } from "flowbite-svelte";
  let buttons = [
    { name: "Profile", mycustomfield: "data1", current: true },
    { name: "Settings", mycustomfield: "data2" },
    { name: "Messages", mycustomfield: "data3" },
    { name: "Download", mycustomfield: "data4", disabled: true, attrs: { type: "submit" } }
  ];
</script>

<Listgroup active items={buttons} horizontal onclick={(e) => alert(Object.entries(e?.detail ?? {}))}></Listgroup>
```

## Advanced

When non standard usage is needed you can omit the `items` props and add elements directly to the list. Usage of hidden so far `ListgroupItem` helps you with proper layout.

```svelte example class="flex justify-center" hideResponsiveButtons
<script>
  import { Listgroup, ListgroupItem, Avatar } from "flowbite-svelte";
  import { TrashBinSolid } from "flowbite-svelte-icons";
</script>

<Listgroup active class="w-48">
  <h3 class="p-1 text-center text-xl font-medium text-gray-900 dark:text-white">User list</h3>
  <ListgroupItem class="gap-2 text-base font-semibold">
    <Avatar src="/images/profile-picture-1.webp" size="xs" />Jese Leos
  </ListgroupItem>
  <ListgroupItem class="gap-2 text-base font-semibold">
    <Avatar src="/images/profile-picture-2.webp" size="xs" />Robert Gouth
  </ListgroupItem>
  <ListgroupItem class="gap-2 text-base font-semibold">
    <Avatar src="/images/profile-picture-3.webp" size="xs" />Bonnie Green
  </ListgroupItem>
  <a href="/" class="flex items-center rounded-b-lg bg-gray-50 p-3 text-sm font-medium text-red-600 hover:bg-gray-100 hover:underline dark:bg-gray-700 dark:text-red-500 dark:hover:bg-gray-600">
    <TrashBinSolid class="ms-1 me-2 h-6 w-6" />
    Delete user
  </a>
</Listgroup>
```

## Component data

The component has the following props, type, and default values. See [types page](/docs/pages/typescript) for type information.

<CompoAttributesViewer {dirName}/>

## References

- [Flowbite List Group](https://flowbite.com/docs/components/list-group/)

<GitHubCompoLinks />
