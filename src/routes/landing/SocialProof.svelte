<script lang="ts">
  import Avatar from "$lib/avatar/Avatar.svelte";
  import Discord from "../utils/icons/Discord.svelte";
  import Figma from "../utils/icons/Figma.svelte";
  import GitHub from "../utils/icons/GitHub.svelte";
  import Npm from "../utils/icons/Npm.svelte";
  import Quote from "../utils/icons/Quote.svelte";
  import Section from "./utils/Section.svelte";
  import { page } from "$app/state";
  import type { PageData } from "../$types";

  let data: PageData = page.data as PageData;

  let github = data.github?.["stargazers_count"] ?? 0;
  let npm = data.npm?.["downloads"] ?? 0;
  let figma = 5400;
  let discord = data.discord?.["approximate_presence_count"] ?? 0;

  function format(x: number) {
    return x.toLocaleString("en", { notation: "standard" });
  }
</script>

<Section>
  <div class="flex flex-col gap-4 lg:flex-row lg:gap-20">
    <div class="mb-4 flex w-full flex-col items-start justify-center gap-3 md:gap-5 lg:mb-0">
      <div class="flex w-full flex-col items-start justify-center gap-6">
        <div class="flex flex-col items-start py-2">
          <Quote />
        </div>
        <div class="flex max-w-2xl flex-col items-start justify-center gap-5 self-stretch pe-8">
          <p class="text-lg leading-relaxed font-medium text-gray-900 dark:text-white">Flowbite provides a robust set of design tokens and components based on the popular Tailwind CSS framework. From the most used UI components like forms and navigation bars to the whole app screens designed both for desktop and mobile, this UI kit provides a solid foundation for any project.</p>
          <p class="text-lg leading-relaxed font-medium text-gray-900 dark:text-white">Designing with Figma components that can be easily translated to the utility classes of Tailwind CSS is a huge timesaver!</p>
        </div>
        <div class="flex flex-row items-center gap-3.5 self-stretch">
          <Avatar src="/images/eugene.jpg" size="xs" />
          <div class="flex items-center gap-3">
            <span class="leading-tight font-semibold text-gray-900 dark:text-white">Eugene Fedorenko</span>
            <span class="leading-tight font-semibold text-gray-900 dark:text-white">/</span>
            <span class="text-sm leading-tight font-normal">Lead designer at Wildbit</span>
          </div>
        </div>
      </div>
    </div>
    <div class="flex w-full flex-col items-start gap-6 md:gap-3">
      <div class="flex flex-row items-start gap-2 self-stretch md:justify-between md:gap-2 md:pe-16 lg:justify-end lg:gap-2 lg:pe-0">
        <a href="https://github.com/themesberg/flowbite-svelte-next" class="flex w-full max-w-[272px] flex-col items-start gap-4 rounded-lg text-gray-400 hover:bg-gray-50 lg:px-8 lg:py-6 dark:hover:bg-gray-800">
          <GitHub />
          <div class="flex flex-col items-start gap-2">
            <p class="text-2xl leading-tight font-bold text-gray-900 dark:text-white">{format(github)}</p>
            <p class="text-sm text-gray-500 md:text-base dark:text-gray-400">Stars on Github</p>
          </div>
        </a>
        <a href="https://npmjs.com/package/flowbite-svelte" class="flex w-full max-w-[272px] flex-col items-start gap-4 rounded-lg text-gray-400 hover:bg-gray-50 lg:px-8 lg:py-6 dark:hover:bg-gray-800">
          <Npm />
          <div class="mt-1 flex flex-col items-start gap-2">
            <p class="text-2xl leading-tight font-bold text-gray-900 dark:text-white">{format(npm)}</p>
            <p class="text-sm text-gray-500 md:text-base dark:text-gray-400">Downloads on NPM</p>
          </div>
        </a>
      </div>
      <div class="flex flex-row items-start gap-2 self-stretch md:justify-between md:gap-12 md:pe-16 lg:justify-end lg:gap-2 lg:pe-0">
        <a href="https://www.figma.com/community/file/1179442320711977498" class="flex w-full max-w-[272px] flex-col items-start gap-4 rounded-lg text-gray-400 hover:bg-gray-50 lg:px-8 lg:py-6 dark:hover:bg-gray-800">
          <Figma />
          <div class="flex flex-col items-start gap-2">
            <p class="text-2xl leading-tight font-bold text-gray-900 dark:text-white">{format(figma)}</p>
            <p class="text-sm text-gray-500 md:text-base dark:text-gray-400">Figma duplicates</p>
          </div>
        </a>
        <a href="https://discord.gg/4eeurUVvTy" rel="nofollow" class="flex w-full max-w-[272px] flex-col items-start gap-4 rounded-lg text-gray-400 hover:bg-gray-50 lg:px-8 lg:py-6 dark:hover:bg-gray-800">
          <Discord />
          <div class="flex flex-col items-start gap-2">
            <p class="text-2xl leading-tight font-bold text-gray-900 dark:text-white">{format(discord)}</p>
            <p class="text-sm text-gray-500 md:text-base dark:text-gray-400">Discord members online</p>
          </div>
        </a>
      </div>
    </div>
  </div>
</Section>
