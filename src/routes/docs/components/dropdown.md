---
layout: componentLayout
title: Svelte Dropdown - Flowbite
breadcrumb_title: Svelte Dropdown
component_title: Dropdown
dir: Components
description: Get started with the dropdown component to show a list of menu items when clicking on the trigger element based on multiple layouts, styles, and placements
thumnailSize: w-28
---

<script>
  import { CompoAttributesViewer,  GitHubCompoLinks, toKebabCase } from '../../utils'
  import { Badge, P, A } from '$lib'
  const dirName = toKebabCase(component_title)
</script>

The dropdown component can be used to show a list of menu items when clicking on an element such as a button and hiding it when clicking outside of the triggering element.

## Setup

```svelte example hideOutput
<script>
  import { Dropdown, DropdownItem, DropdownDivider, DropdownHeader } from 'flowbite-svelte';
</script>
```

## Examples

If you want to show a dropdown menu when clicking on an element add the `Dropdown` and `DropdownItem` components.

```svelte example class="flex justify-center items-start h-64" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem } from 'flowbite-svelte';
  import { ChevronDownOutline } from 'flowbite-svelte-icons';
</script>

<Button>Dropdown button<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
<Dropdown simple>
  <DropdownItem>Dashboard</DropdownItem>
  <DropdownItem>Settings</DropdownItem>
  <DropdownItem>Earnings</DropdownItem>
  <DropdownItem>Sign out</DropdownItem>
</Dropdown>
```

## Adding links and active class

Utilize the `href` prop within the `DropdownItem` component to incorporate a hyperlink. To initiate the application of the active class, include the `activeUrl` prop within the `Dropdown` component:

```svelte example class="flex justify-center items-start h-64" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem } from 'flowbite-svelte';
  import { ChevronDownOutline } from 'flowbite-svelte-icons';
  import { page } from '$app/stores';
  $: activeUrl = $page.url.pathname;
</script>

<Button>Dropdown button<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
<Dropdown {activeUrl} simple>
  <DropdownItem href="/">Home</DropdownItem>
  <DropdownItem href="/docs/components/dropdown">Dropdown</DropdownItem>
  <DropdownItem href="/docs/components/accordion">Accordion</DropdownItem>
  <DropdownItem href="/docs/components/alert">Alert</DropdownItem>
</Dropdown>
```

To change the active class, use the `activeClass` prop:

```svelte example class="flex justify-center items-start h-64" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem } from 'flowbite-svelte';
  import { ChevronDownOutline } from 'flowbite-svelte-icons';
  import { page } from '$app/stores';
  $: activeUrl = $page.url.pathname;
  let activeClass = 'text-green-500 dark:text-green-300 hover:text-green-700 dark:hover:text-green-500';
</script>

<Button>Dropdown button<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
<Dropdown {activeUrl} {activeClass} simple>
  <DropdownItem href="/">Home</DropdownItem>
  <DropdownItem href="/docs/components/dropdown">Dropdown</DropdownItem>
  <DropdownItem href="/docs/components/accordion">Accordion</DropdownItem>
  <DropdownItem href="/docs/components/alert">Alert</DropdownItem>
</Dropdown>
```

## Dropdown divider

You can use the `DropdownDivider` component to add separate elements inside the dropdown menu. Note that you have a natural divider between main content of the `Dropdown` and its header and footer.

```svelte example class="flex justify-center items-start h-64" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, DropdownDivider } from 'flowbite-svelte';
  import { ChevronDownOutline } from 'flowbite-svelte-icons';
</script>

<Button>Dropdown button<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
<Dropdown simple>
  <DropdownItem>Dashboard</DropdownItem>
  <DropdownDivider />
  <DropdownItem>Settings</DropdownItem>
  <DropdownItem>Earnings</DropdownItem>
  <DropdownItem>Separated link</DropdownItem>
</Dropdown>
```

## Dropdown header

Use this example to show extra information outside of the list of menu items inside the dropdown.

```svelte example class="flex justify-center items-start h-80" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, DropdownDivider, DropdownGroup, DropdownHeader } from 'flowbite-svelte';
  import { ChevronDownOutline } from 'flowbite-svelte-icons';
</script>

<Button>Dropdown button<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
<Dropdown>
  <DropdownHeader>
    <span class="block text-sm text-gray-900 dark:text-white">Bonnie Green</span>
    <span class="block truncate text-sm font-medium">name@flowbite.com</span>
  </DropdownHeader>
  <DropdownGroup>
    <DropdownItem>Dashboard</DropdownItem>
    <DropdownItem>Settings</DropdownItem>
    <DropdownItem>Earnings</DropdownItem>
    <DropdownItem>Sign out</DropdownItem>
  </DropdownGroup>
</Dropdown>
```

## Multi-level dropdown

Use this example to enable multi-level dropdown menus by adding stacked elements inside of each other.

```svelte example class="flex justify-center items-start h-64" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, DropdownDivider } from 'flowbite-svelte';
  import { ChevronDownOutline, ChevronRightOutline } from 'flowbite-svelte-icons';
</script>

<Button>Dropdown button<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
<Dropdown simple>
  <DropdownItem>Dashboard</DropdownItem>
  <DropdownItem class="flex items-center justify-between">
    Dropdown<ChevronRightOutline class="w-6 h-6 ms-2 text-primary-700 dark:text-white" />
  </DropdownItem>
  <Dropdown simple placement="right-start">
    <DropdownItem>Overview</DropdownItem>
    <DropdownItem>My downloads</DropdownItem>
    <DropdownItem>Billing</DropdownItem>
  </Dropdown>
  <DropdownItem>Earnings</DropdownItem>
  <DropdownItem>Sign out</DropdownItem>
</Dropdown>
```

## Programatic open/close

When you want to control your dropdown open status via javascript code you can bind to `open` property.

```svelte example class="flex justify-center items-start h-64" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, DropdownDivider } from 'flowbite-svelte';
  import { ChevronDownOutline, ChevronRightOutline } from 'flowbite-svelte-icons';
  let dropdownOpen = false;
</script>

<Button>Dropdown button<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
<Dropdown bind:open={dropdownOpen} simple>
  <DropdownItem on:click={() => (dropdownOpen = false)}>Dashboard (close)</DropdownItem>
  <DropdownItem class="flex items-center justify-between">
    Dropdown<ChevronRightOutline class="w-6 h-6 ms-2 text-primary-700 dark:text-white" />
  </DropdownItem>
  <Dropdown simple placement="right-start">
    <DropdownItem on:click={() => (dropdownOpen = false)}>Overview (close)</DropdownItem>
    <DropdownItem>My downloads</DropdownItem>
    <DropdownItem>Billing</DropdownItem>
  </Dropdown>
  <DropdownItem>Earnings</DropdownItem>
  <DropdownItem>Sign out</DropdownItem>
</Dropdown>
```

## Dropdown with checkbox

Add multiple checkbox elements inside your dropdown menu to enable more advanced input interaction.

```svelte example class="flex justify-center items-start h-52" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, Checkbox } from 'flowbite-svelte';
  import { ChevronDownOutline } from 'flowbite-svelte-icons';
</script>

<Button>Dropdown checkbox<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
<Dropdown simple class="w-44 p-3 space-y-3 text-sm">
  <li>
    <Checkbox>Default checkbox</Checkbox>
  </li>
  <li>
    <Checkbox checked>Checked state</Checkbox>
  </li>
  <li>
    <Checkbox>Default checkbox</Checkbox>
  </li>
</Dropdown>
```

### Background hover

Use this example to update the background color of a menu item when using a list of checkbox elements.

```svelte example class="flex justify-center items-start h-56" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, Checkbox } from 'flowbite-svelte';
  import { ChevronDownOutline } from 'flowbite-svelte-icons';
</script>

<Button>Dropdown checkbox<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
<Dropdown simple class="w-48 p-3 space-y-1 text-sm">
  <li class="rounded-sm p-2 hover:bg-gray-100 dark:hover:bg-gray-600">
    <Checkbox>Default checkbox</Checkbox>
  </li>
  <li class="rounded-sm p-2 hover:bg-gray-100 dark:hover:bg-gray-600">
    <Checkbox checked>Checked state</Checkbox>
  </li>
  <li class="rounded-sm p-2 hover:bg-gray-100 dark:hover:bg-gray-600">
    <Checkbox>Default checkbox</Checkbox>
  </li>
</Dropdown>
```

### Helper text

Add an extra helper text to each checkbox element inside the dropdown menu list with this example.

```svelte example class="flex justify-center items-start h-96" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, Checkbox, Helper } from 'flowbite-svelte';
  import { ChevronDownOutline } from 'flowbite-svelte-icons';
</script>

<Button>Dropdown checkbox<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
<Dropdown simple class="w-60 p-3 space-y-1 text-sm">
  <li class="rounded-sm p-2 hover:bg-gray-100 dark:hover:bg-gray-600">
    <Checkbox>Enable notifications</Checkbox>
    <Helper class="ps-6">Some helpful instruction goes over here.</Helper>
  </li>
  <li class="rounded-sm p-2 hover:bg-gray-100 dark:hover:bg-gray-600">
    <Checkbox checked>Enable 2FA auth</Checkbox>
    <Helper class="ps-6">Some helpful instruction goes over here.</Helper>
  </li>
  <li class="rounded-sm p-2 hover:bg-gray-100 dark:hover:bg-gray-600">
    <Checkbox>Subscribe newsletter</Checkbox>
    <Helper class="ps-6">Some helpful instruction goes over here.</Helper>
  </li>
</Dropdown>
```

## Dropdown with radio

Add multiple radio elements inside your dropdown menu to enable more advanced input interaction.

```svelte example class="flex justify-center items-start h-64" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, Radio } from 'flowbite-svelte';
  import { ChevronDownOutline } from 'flowbite-svelte-icons';
  let group1 = 2;
</script>

<Button>
  Dropdown radio {group1}<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" />
</Button>
<Dropdown simple class="w-44 p-3 space-y-3 text-sm">
  <li>
    <Radio name="group1" bind:group={group1} value={1}>Default radio</Radio>
  </li>
  <li>
    <Radio name="group1" bind:group={group1} value={2}>Checked state</Radio>
  </li>
  <li>
    <Radio name="group1" bind:group={group1} value={3}>Default radio</Radio>
  </li>
</Dropdown>
```

### Background hover

Use this example to update the background color of a menu item when using a list of radio elements.

```svelte example class="flex justify-center items-start h-64" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, Radio } from 'flowbite-svelte';
  import { ChevronDownOutline } from 'flowbite-svelte-icons';
  let group2 = 2;
</script>

<Button>Dropdown radio<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
<Dropdown simple class="w-48 p-3 space-y-1">
  <li class="rounded-sm p-2 hover:bg-gray-100 dark:hover:bg-gray-600">
    <Radio name="group2" bind:group={group2} value={1}>Default radio</Radio>
  </li>
  <li class="rounded-sm p-2 hover:bg-gray-100 dark:hover:bg-gray-600">
    <Radio name="group2" bind:group={group2} value={2}>Checked state</Radio>
  </li>
  <li class="rounded-sm p-2 hover:bg-gray-100 dark:hover:bg-gray-600">
    <Radio name="group2" bind:group={group2} value={3}>Default radio</Radio>
  </li>
</Dropdown>
```

### Helper text

Add an extra helper text to each radio element inside the dropdown menu list with this example.

```svelte example class="flex justify-center items-start h-96" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, Radio, Helper } from 'flowbite-svelte';
  import { ChevronDownOutline } from 'flowbite-svelte-icons';
  let group3 = 2;
</script>

<Button>Dropdown radio<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
<Dropdown simple class="w-60 p-3 space-y-1">
  <li class="rounded-sm p-2 hover:bg-gray-100 dark:hover:bg-gray-600">
    <Radio name="group3" bind:group={group3} value={1}>Enable notifications</Radio>
    <Helper class="ps-6">Some helpful instruction goes over here.</Helper>
  </li>
  <li class="rounded-sm p-2 hover:bg-gray-100 dark:hover:bg-gray-600">
    <Radio name="group3" bind:group={group3} value={2}>Enable 2FA auth</Radio>
    <Helper class="ps-6">Some helpful instruction goes over here.</Helper>
  </li>
  <li class="rounded-sm p-2 hover:bg-gray-100 dark:hover:bg-gray-600">
    <Radio name="group3" bind:group={group3} value={3}>Subscribe newsletter</Radio>
    <Helper class="ps-6">Some helpful instruction goes over here.</Helper>
  </li>
</Dropdown>
```

## Dropdown with toggle switch

Show a list of toggle switch elements inside the dropdown menu to enable a yes or no type of choice.

```svelte example class="flex justify-center items-start h-64" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, Toggle } from 'flowbite-svelte';
  import { ChevronDownOutline } from 'flowbite-svelte-icons';
  let group2 = 2;
</script>

<Button>Dropdown toggle<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
<Dropdown simple class="w-56 p-3 space-y-1">
  <li>
    <Toggle class="rounded-sm p-2 hover:bg-gray-100 dark:hover:bg-gray-600">Default toggle</Toggle>
  </li>
  <li>
    <Toggle class="rounded-sm p-2 hover:bg-gray-100 dark:hover:bg-gray-600" checked>Checked state</Toggle>
  </li>
  <li>
    <Toggle class="rounded-sm p-2 hover:bg-gray-100 dark:hover:bg-gray-600">Default toggle</Toggle>
  </li>
</Dropdown>
```

## Dropdown navbar

<p>You can also use the dropdown element inside a navigation bar and add a second level of navigation hierarchy, but make sure to use Navbar components.</p>

```svelte example class="flex justify-center items-start h-96" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, DropdownDivider, Navbar, NavBrand, NavHamburger, NavUl, NavLi } from 'flowbite-svelte';
  import { ChevronDownOutline } from 'flowbite-svelte-icons';
  let group3 = 2;
</script>

<Navbar >
  <NavBrand href="/">
    <img src="/images/flowbite-svelte-icon-logo.svg" class="me-3 h-6 sm:h-9" alt="Flowbite Logo" />
    <span class="self-center whitespace-nowrap text-xl font-semibold dark:text-white">Flowbite</span>
  </NavBrand>
  <NavHamburger />
  <NavUl class="ms-3 pt-6">
    <NavLi href="/" active={true}>Home</NavLi>
    <NavLi class="cursor-pointer">
      Dropdown<ChevronDownOutline class="w-6 h-6 ms-2 text-primary-800 dark:text-white inline" />
    </NavLi>
    <Dropdown simple>
      <DropdownItem>Dashboard</DropdownItem>
      <DropdownItem>Settings</DropdownItem>
      <DropdownItem>Earnings</DropdownItem>
      <DropdownItem>Sign out</DropdownItem>
    </Dropdown>
    <NavLi href="/services">Services</NavLi>
    <NavLi href="/pricing">Pricing</NavLi>
    <NavLi href="/contact">Contact</NavLi>
  </NavUl>
</Navbar>
```

## Dropdown with scrolling

This example can be used when you want to show a long list of items that won’t affect the height of the dropdown menu by enabling a scrolling behaviour.

```svelte example class="flex justify-center items-start h-80" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, DropdownGroup, Avatar } from 'flowbite-svelte';
  import { ChevronDownOutline } from 'flowbite-svelte-icons';
</script>

<Button>Project users<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
<Dropdown class="w-48 overflow-y-auto py-1 h-48">
  <DropdownGroup>
    <DropdownItem class="flex items-center text-base font-semibold gap-2">
      <Avatar src="/images/profile-picture-1.webp" size="xs" />Jese Leos
    </DropdownItem>
    <DropdownItem class="flex items-center text-base font-semibold gap-2">
      <Avatar src="/images/profile-picture-2.webp" size="xs" />Robert Gouth
    </DropdownItem>
    <DropdownItem class="flex items-center text-base font-semibold gap-2">
      <Avatar src="/images/profile-picture-3.webp" size="xs" />Bonnie Green
    </DropdownItem>
    <DropdownItem class="flex items-center text-base font-semibold gap-2">
      <Avatar src="/images/profile-picture-1.webp" size="xs" />Robert Wall
    </DropdownItem>
    <DropdownItem class="flex items-center text-base font-semibold gap-2">
      <Avatar src="/images/profile-picture-2.webp" size="xs" />Joseph Mcfall
    </DropdownItem>
    <DropdownItem class="flex items-center text-base font-semibold gap-2">
      <Avatar src="/images/profile-picture-3.webp" size="xs" />Leslie Livingston
    </DropdownItem>
  </DropdownGroup>
  <a href="/" class="flex items-center px-3 py-2 -mb-1 text-sm font-medium text-primary-600 bg-gray-50 hover:bg-gray-100 dark:bg-gray-700 dark:hover:bg-gray-600 dark:text-primary-500 hover:underline">
    <ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" />Add new user
  </a>
</Dropdown>
```

## Dropdown with search

Use this example if you want to add a search bar inside the dropdown menu to be able to filter through a long list of menu items with scrolling behaviour.

```svelte example class="flex justify-center items-start h-96" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, DropdownHeader, DropdownGroup, Checkbox, Search } from 'flowbite-svelte';
  import { ChevronDownOutline, UserRemoveSolid } from 'flowbite-svelte-icons';
  let searchTerm = ''
  const people = [
    { name: 'Robert Gouth', checked: false },
    { name: 'Jese Leos', checked: false },
    { name: 'Bonnie Green', checked: true },
  ]
  $: filteredItems = people.filter((person) => person.name.toLowerCase().indexOf(searchTerm?.toLowerCase()) !== -1);
</script>

<Button>Dropdown search<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
<Dropdown>
  <div class="p-3">
    <Search size="md" bind:value={searchTerm}/>
  </div>
  <DropdownGroup class="overflow-y-auto h-24">
  {#each filteredItems as person (person.name)}
    <li class="rounded-sm p-2 hover:bg-gray-100 dark:hover:bg-gray-600">
      <Checkbox bind:checked={person.checked}>{person.name}</Checkbox>
    </li>
  {/each}
  </DropdownGroup>
  <a href="/" class="flex items-center p-3 -mb-1 text-sm font-medium text-red-600 bg-gray-50 hover:bg-gray-100 dark:bg-gray-700 dark:hover:bg-gray-600 dark:text-red-500 hover:underline">
    <UserRemoveSolid class="w-4 h-4 me-2 text-primary-700 dark:text-primary-700" />Delete user
  </a>
</Dropdown>
```

## Menu icon

Use the menu icon trigger element on components such as cards as an alternative element to the button.

```svelte example class="flex justify-center items-start gap-4 h-60" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, ToolbarButton, DropdownDivider } from 'flowbite-svelte';
  import { DotsHorizontalOutline, DotsVerticalOutline } from 'flowbite-svelte-icons';
</script>

<DotsHorizontalOutline class="dots-menu dark:text-white" />
<DotsVerticalOutline class="dots-menu dark:text-white" />
<Dropdown simple triggeredBy=".dots-menu">
  <DropdownItem>Dashboard</DropdownItem>
  <DropdownItem>Settings</DropdownItem>
  <DropdownItem>Earnings</DropdownItem>
  <DropdownItem>Sign out</DropdownItem>
</Dropdown>
```

## Notification bell

Use this example to show a list of notifications inside your application by providing more detailed information such as the user avatar, content and time of notification triggered by a notification bell icon.

```svelte example class="flex justify-center items-start h-96" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, DropdownHeader, DropdownGroup, Avatar } from 'flowbite-svelte';
  import { BellSolid, EyeSolid } from 'flowbite-svelte-icons';
</script>

<div id="bell" class="inline-flex items-center text-sm font-medium text-center text-gray-500 hover:text-gray-900 focus:outline-hidden dark:hover:text-white dark:text-gray-400">
  <BellSolid class="w-8 h-8" />
  <div class="flex relative">
    <div class="inline-flex relative -top-2 end-4 w-3 h-3 bg-red-500 rounded-full border-2 border-white dark:border-gray-900"></div>
  </div>
</div>
<Dropdown triggeredBy="#bell" class="w-full max-w-sm rounded-sm divide-y divide-gray-100 shadow-sm dark:bg-gray-800 dark:divide-gray-700">
  <div class="text-center py-2 font-bold">Notifications</div>
  <DropdownGroup>
    <DropdownItem class="flex space-x-4 rtl:space-x-reverse">
      <Avatar src="/images/profile-picture-1.webp" dot={{ color: 'bg-gray-300' }} rounded />
      <div class="ps-3 w-full">
        <div class="text-gray-500 text-sm mb-1.5 dark:text-gray-400">
          New message from <span class="font-semibold text-gray-900 dark:text-white">Jese Leos</span>
          : "Hey, what's up? All set for the presentation?"
        </div>
        <div class="text-xs text-primary-600 dark:text-primary-500">a few moments ago</div>
      </div>
    </DropdownItem>
    <DropdownItem class="flex space-x-4 rtl:space-x-reverse">
      <Avatar src="/images/profile-picture-2.webp" dot={{ color: 'bg-red-400' }} rounded />
      <div class="ps-3 w-full">
        <div class="text-gray-500 text-sm mb-1.5 dark:text-gray-400">
          <span class="font-semibold text-gray-900 dark:text-white">Joseph Mcfall</span>
          and
          <span class="font-medium text-gray-900 dark:text-white">5 others</span>
          started following you.
        </div>
        <div class="text-xs text-primary-600 dark:text-primary-500">10 minutes ago</div>
      </div>
    </DropdownItem>
    <DropdownItem class="flex space-x-4 rtl:space-x-reverse">
      <Avatar src="/images/profile-picture-3.webp" dot={{ color: 'bg-green-400' }} rounded />
      <div class="ps-3 w-full">
        <div class="text-gray-500 text-sm mb-1.5 dark:text-gray-400">
          <span class="font-semibold text-gray-900 dark:text-white">Bonnie Green</span>
          and
          <span class="font-medium text-gray-900 dark:text-white">141 others</span>
          love your story. See it and view more stories.
        </div>
        <div class="text-xs text-primary-600 dark:text-primary-500">44 minutes ago</div>
      </div>
    </DropdownItem>
  </DropdownGroup>
  <a href="/" class="block py-2 -my-1 text-sm font-medium text-center text-gray-900 bg-gray-50 hover:bg-gray-100 dark:bg-gray-800 dark:hover:bg-gray-700 dark:text-white">
    <div class="inline-flex items-center">
      <EyeSolid class="me-2 w-4 h-4 text-gray-500 dark:text-gray-400" />
      View all
    </div>
  </a>
</Dropdown>
```

## User avatar

This example can be used to show a list of menu items and options when a user is logged into your application.

```svelte example class="flex justify-center items-start h-80" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, Avatar, DropdownHeader, DropdownGroup, DropdownDivider } from 'flowbite-svelte';
</script>

<Avatar class="acs" src="/images/profile-picture-3.webp" dot={{ color: 'green' }} />
<Dropdown triggeredBy=".acs">
  <DropdownHeader>
    <span class="block text-sm text-gray-900 dark:text-white">Bonnie Green</span>
    <span class="block truncate text-sm font-medium">name@flowbite.com</span>
  </DropdownHeader>
  <DropdownGroup>
    <DropdownItem>Dashboard</DropdownItem>
    <DropdownItem>Settings</DropdownItem>
    <DropdownItem>Earnings</DropdownItem>
    <DropdownItem>Sign out</DropdownItem>
  </DropdownGroup>
</Dropdown>
```

## Avatar with name

Use this example to also show the name or email of the user next to the avatar for the dropdown menu.

```svelte example class="flex justify-center items-start h-80" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, Avatar, DropdownHeader, DropdownGroup } from 'flowbite-svelte';
</script>

<Button pill color="light" id="avatar_with_name" class="p-1!">
  <Avatar src="/images/profile-picture-3.webp" class="me-2" />
  Bonnie Green
</Button>
<Dropdown inline triggeredBy="#avatar_with_name">
  <DropdownHeader>
    <span class="block text-sm text-gray-900 dark:text-white">Bonnie Green</span>
    <span class="block truncate text-sm font-medium">name@flowbite.com</span>
  </DropdownHeader>
  <DropdownGroup>
    <DropdownItem>Dashboard</DropdownItem>
    <DropdownItem>Settings</DropdownItem>
    <DropdownItem>Earnings</DropdownItem>
  </DropdownGroup>
  <DropdownHeader>Sign out</DropdownHeader>
</Dropdown>
```

## Sizes

<p>The dropdown menus work with buttons of all sizes including smaller or larger ones.</p>

```svelte example class="flex justify-center items-start gap-4 h-80" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, DropdownHeader, DropdownGroup } from 'flowbite-svelte';
  import { ChevronDownOutline } from 'flowbite-svelte-icons';
</script>

<Dropdown triggeredBy=".sizes">
  <DropdownGroup>
    <DropdownItem>Dashboard</DropdownItem>
    <DropdownItem>Settings</DropdownItem>
    <DropdownItem>Earnings</DropdownItem>
  </DropdownGroup>
  <DropdownHeader>Sign out</DropdownHeader>
</Dropdown>
<Button class="sizes" size="sm">
  Small dropdown<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" />
</Button>
<Button class="sizes" size="lg">
  Large dropdown<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" />
</Button>
```

## Placement

You can also use the `placement={top|right|bottom|left}` options to choose the placement of the dropdown menu. By default the positioning is set to the bottom side of the button.

```svelte example hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem } from 'flowbite-svelte';
  import { ChevronDownOutline, ChevronUpOutline, ChevronRightOutline, ChevronLeftOutline } from 'flowbite-svelte-icons';
  let placement = 'left';
</script>

<Dropdown simple placement='top' triggeredBy="#top-dd">
  <DropdownItem>Dashboard</DropdownItem>
  <DropdownItem>Settings</DropdownItem>
  <DropdownItem>Earnings</DropdownItem>
  <DropdownItem>Sign out</DropdownItem>
</Dropdown>
<Dropdown simple placement='bottom' triggeredBy="#bottom-dd">
  <DropdownItem>Dashboard</DropdownItem>
  <DropdownItem>Settings</DropdownItem>
  <DropdownItem>Earnings</DropdownItem>
  <DropdownItem>Sign out</DropdownItem>
</Dropdown>
<Dropdown simple placement='right' triggeredBy="#right-dd">
  <DropdownItem>Dashboard</DropdownItem>
  <DropdownItem>Settings</DropdownItem>
  <DropdownItem>Earnings</DropdownItem>
  <DropdownItem>Sign out</DropdownItem>
</Dropdown>
<Dropdown simple placement='left' triggeredBy="#left-dd">
  <DropdownItem>Dashboard</DropdownItem>
  <DropdownItem>Settings</DropdownItem>
  <DropdownItem>Earnings</DropdownItem>
  <DropdownItem>Sign out</DropdownItem>
</Dropdown>

<!-- svelte-ignore a11y-no-static-element-interactions -->
<div id="placements" class="flex flex-col justify-center items-center gap-2 h-96 my-8">
  <Button id='top-dd'>Dropdown top<ChevronUpOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
  <div class="flex space-x-2 rtl:space-x-reverse">
    <Button id='left-dd'><ChevronLeftOutline class="w-6 h-6 me-2 text-white dark:text-white" />Dropdown left</Button>
    <Button id='right-dd'>Dropdown right<ChevronRightOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
  </div>
  <Button id='bottom-dd'>Dropdown bottom<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
</div>
```

## Double placement

As dropdown is implemented using the [Floating UI](https://floating-ui.com) library, placement can be further specified by using the `Placement` type defined in [Floating UI docs](https://floating-ui.com/docs/computePosition#placement)

```svelte example class="flex justify-center items-center gap-2 h-96" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem } from 'flowbite-svelte';
  import { ChevronDownOutline, ChevronUpOutline } from 'flowbite-svelte-icons';
  let placement = 'left';
</script>

<!-- svelte-ignore a11y-no-static-element-interactions -->
<div on:mousedown={(e) => (placement = e.target.dataset.placement)}>
  <Button data-placement="left-start">
    Dropdown left start<ChevronUpOutline class="w-6 h-6 ms-2 text-white dark:text-white" />
  </Button>
  <Button data-placement="right-end">
    Dropdown right end<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" />
  </Button>
</div>

<Dropdown simple {placement} triggeredBy="[data-placement]">
  <DropdownItem>Dashboard</DropdownItem>
  <DropdownItem>Settings</DropdownItem>
  <DropdownItem>Earnings</DropdownItem>
  <DropdownItem>Sign out</DropdownItem>
</Dropdown>
```

## Events

`DropdownItem` renders to link or button wrapped with `<li/>` element depending whether you supplied the `href` property. Therefore you can catch standard events on it like `on:click`.

```svelte example class="flex justify-center items-start h-40" hideResponsiveButtons
<script>
  import { Button, Dropdown, DropdownItem, Checkbox } from 'flowbite-svelte';
  import { ChevronDownOutline } from 'flowbite-svelte-icons';
  const handleClick = (e) => {
    e.preventDefault();
    alert('Clicked on: ' + e.target);
  };
</script>

<Button>Dropdown button<ChevronDownOutline class="w-6 h-6 ms-2 text-white dark:text-white" /></Button>
<Dropdown simple>
  <DropdownItem href="/link" onclick={handleClick}>Rendered as link</DropdownItem>
  <DropdownItem onclick={handleClick}>Rendered as button</DropdownItem>
</Dropdown>
```

## Component data

The component has the following props, type, and default values. See [types page](/docs/pages/typescript) for type information.

### Dropdown styling

- Use the `class` prop to style underlying `ul` element.
- Use the `classContainer` prop to overwrite `containerClass`.
- Use the `classHeader` prop to overwrite `headerClass`.
- Use the `classFooter` prop to overwrite `footerClass`.

### DropdownDivider styling

- Use the `class` prop to overwrite `divClass`.

### DropdownHeader styling

- Use the `class` prop to overwrite `divClass`.

### DropdownItem styling

- Use the `class` prop to overwrite `defaultClass`.

<CompoAttributesViewer {dirName}/>

## References

- [Flowbite Dropdown](https://flowbite.com/docs/components/drawer/)

<GitHubCompoLinks />
