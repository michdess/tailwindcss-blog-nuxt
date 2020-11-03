<template>
  <header class="flex justify-between items-center py-10">
    <div>
      <a href="/">
        <a aria-label="Tailwind CSS Blog">
          <TailwindMark class="h-6 sm:hidden" />
          <TailwindLogo class="hidden sm:block h-6" />
        </a>
      </a>
    </div>
    <div class="text-base leading-5">
      <a
        href="https://tailwindcss.com"
        class="font-medium text-gray-500 hover:text-gray-700"
      >
        Documentation &rarr;
      </a>
    </div>
  </header>
</template>
<script>
import TailwindLogo from './TailwindLogo'
import TailwindMark from './TailwindMark'
export default {
  components: {
    TailwindLogo,
    TailwindMark,
  },
}
</script>
