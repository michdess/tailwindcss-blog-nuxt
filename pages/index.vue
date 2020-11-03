<template>
  <div class="divide-y divide-gray-200">
    <Head>
      <meta name="twitter:card" content="summary_large_image" />
      <meta name="twitter:site" content="@tailwindcss" />
      <meta name="twitter:creator" content="@tailwindcss" />
      <meta name="twitter:title" content="Blog – Tailwind CSS" />
      <meta
        name="twitter:description"
        content="News content from the Tailwind CSS team."
      />
      <meta
        name="twitter:image"
        :content="'https://blog.tailwindcss.com' + twitterCard"
      />
      <meta property="og:url" content="https://blog.tailwindcss.com" />
      <meta property="og:type" content="article" />
      <meta property="og:title" content="Blog – Tailwind CSS" />
      <meta
        property="og:description"
        content="News content from the Tailwind CSS team."
      />
      <meta
        property="og:image"
        :content="'https://blog.tailwindcss.com' + twitterCard"
      />
      <title>Blog – Tailwind CSS</title>
      <meta
        name="description"
        content="News content from the Tailwind CSS team."
      />
    </Head>
    <div class="pt-6 pb-8 space-y-2 md:space-y-5">
      <h1
        class="text-3xl leading-9 font-extrabold text-gray-900 tracking-tight sm:text-4xl sm:leading-10 md:text-6xl md:leading-14"
      >
        Latest
      </h1>
      <p class="text-lg leading-7 text-gray-500">
        All the latest Tailwind CSS news, straight from the team.
      </p>
    </div>
    <ul class="divide-y divide-gray-200">
      <li
        :key="index"
        class="py-12"
        v-for="({ link, module: { default: Component, meta } }, index) in posts"
      >
        <article
          class="space-y-2 xl:grid xl:grid-cols-4 xl:space-y-0 xl:items-baseline"
        >
          <dl>
            <dt class="sr-only">Published on</dt>
            <dd class="text-base leading-6 font-medium text-gray-500">
              <time dateTime="{post.module.meta.date}">{{
                postDateTemplate.render(new Date(meta.date))
              }}</time>
            </dd>
          </dl>
          <div class="space-y-5 xl:col-span-3">
            <div class="space-y-6">
              <h2 class="text-2xl leading-8 font-bold tracking-tight">
                <NuxtLink :to="link">
                  <a class="text-gray-900">{{ meta.title }}</a>
                </NuxtLink>
              </h2>
              <div class="prose max-w-none text-gray-500">
                <Component />
              </div>
            </div>
            <div class="text-base leading-6 font-medium">
              <NuxtLink :to="link">
                <a
                  class="text-teal-500 hover:text-teal-600"
                  :aria-label="'Read ' + meta.title"
                >
                  Read more &rarr;
                </a>
              </NuxtLink>
            </div>
          </div>
        </article>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import getAllPostPreviews from '../utils/getAllPostPreviews'
import tinytime from 'tinytime'

export default Vue.extend({
  data() {
    return {
      twitterCard: '../../img/twitter-card.jpg',
      posts: null,
      postDateTemplate: tinytime('{MMMM} {DD}, {YYYY}'),
    }
  },
  mounted() {
    this.posts = getAllPostPreviews()
  },
})
</script>
