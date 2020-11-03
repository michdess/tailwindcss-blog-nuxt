<template>
  <article class="xl:divide-y xl:divide-gray-200">
    <Head>
      <title>{meta.title} – Tailwind CSS</title>
      <meta name="twitter:card" content="summary_large_image" />
      <meta name="twitter:site" content="@tailwindcss" />
      <meta name="twitter:creator" content="@tailwindcss" />
      <!-- <meta name="twitter:title" content={`${meta.title} – Tailwind CSS`} /> -->
      <meta name="twitter:description" content="{meta.description}" />
      <!-- <meta name="twitter:image" content={`https://blog.tailwindcss.com${meta.image}`} />
        <meta property="og:url" content={`https://blog.tailwindcss.com${router.pathname}`} /> -->
      <meta property="og:type" content="article" />
      <!-- <meta property="og:title" content={`${meta.title} – Tailwind CSS`} /> -->
      <meta property="og:description" content="{meta.description}" />
      <!-- <meta property="og:image" content={`https://blog.tailwindcss.com${meta.image}`} /> -->
      <!-- <meta name="description" content={meta.description}></meta> -->
    </Head>
    <header class="pt-6 xl:pb-10">
      <div class="space-y-1 text-center">
        <dl class="space-y-10">
          <div>
            <dt class="sr-only">Published on</dt>
            <dd class="text-base leading-6 font-medium text-gray-500">
              <time dateTime="{meta.date}"
                >{postDateTemplate.render(new Date(meta.date))}</time
              >
            </dd>
          </div>
        </dl>
        <div>
          <PageTitle>{{ meta.title }}</PageTitle>
        </div>
      </div>
    </header>
    <div
      class="divide-y xl:divide-y-0 divide-gray-200 xl:grid xl:grid-cols-4 xl:col-gap-6 pb-16 xl:pb-20"
      style="grid-template-rows: 'auto 1fr'"
    >
      <dl class="pt-6 pb-10 xl:pt-11 xl:border-b xl:border-gray-200">
        <dt class="sr-only">Authors</dt>
        <dd>
          <ul
            class="flex justify-center xl:block space-x-8 sm:space-x-12 xl:space-x-0 xl:space-y-8"
          >
            <li
              v-for="author in meta.authors"
              :key="author.twitter"
              class="flex items-center space-x-2"
            >
              <img :src="author.avatar" alt="" class="w-10 h-10 rounded-full" />
              <dl class="text-sm font-medium leading-5 whitespace-no-wrap">
                <dt class="sr-only">Name</dt>
                <dd class="text-gray-900">{{ author.name }}</dd>
                <dt class="sr-only">Twitter</dt>
                <dd>
                  <a
                    :href="'https://twitter.com/' + author.twitter"
                    class="text-teal-500 hover:text-teal-600"
                  >
                    {{ author.twitter }}
                  </a>
                </dd>
              </dl>
            </li>
          </ul>
        </dd>
      </dl>
      <div class="divide-y divide-gray-200 xl:pb-0 xl:col-span-3 xl:row-span-2">
        <div class="prose max-w-none pt-10 pb-8">
          <MDXProvider :components="mdxComponents">{children}</MDXProvider>
        </div>
        <!-- {meta.discussion && (
            <div class="pt-6 pb-16">
              <p>
                Want to talk about this post?{' '}
                <a href={meta.discussion} class="font-medium text-teal-500 hover:text-teal-600">
                  Discuss this on GitHub &rarr;
                </a>
              </p>
            </div>
          )} -->
      </div>
      <!-- <footer class="text-sm font-medium leading-5 divide-y divide-gray-200 xl:col-start-1 xl:row-start-2">
          {(next || previous) && (
            <div class="space-y-8 py-8">
              {next && (
                <div>
                  <h2 class="text-xs tracking-wide uppercase text-gray-500">Next Article</h2>
                  <div class="text-teal-500 hover:text-teal-600">
                    <Link href={next.link}>
                      <a>{next.title}</a>
                    </Link>
                  </div>
                </div>
              )}
              {previous && (
                <div>
                  <h2 class="text-xs tracking-wide uppercase text-gray-500">
                    Previous Article
                  </h2>
                  <div class="text-teal-500 hover:text-teal-600">
                    <Link href={previous.link}>
                      <a>{previous.title}</a>
                    </Link>
                  </div>
                </div>
              )}
            </div>
          )}
          <div class="pt-8">
            <Link href="/">
              <a class="text-teal-500 hover:text-teal-600">&larr; Back to the blog</a>
            </Link>
          </div>
        </footer> -->
    </div>
  </article>
</template>
<script>
// import Head from 'next/head'
import PageTitle from './PageTitle'
import tinytime from 'tinytime'
// import Link from 'next/link'
// import { useRouter } from 'next/router'
import { MDXProvider } from '@mdx-js/vue'
// const mdxComponents = {
//   pre: ({ class, ...props }) => (
//     <pre class={`${class} rounded-md bg-gray-800 py-3 px-4 overflow-x-auto`} {...props} />
//   ),
//   'pre.code': ({ class, ...props }) => (
//     <code class={`${class} text-gray-200`} {...props} />
//   ),
// }
// const router = useRouter()
// const postIndex = posts.findIndex((post) => post.link === router.pathname)
// const previous = posts[postIndex + 1]
// const next = posts[postIndex - 1]

export default {
  props: ['meta'],
  data() {
    return {
      postDateTemplate: tinytime('{dddd}, {MMMM} {DD}, {YYYY}'),
    }
  },
}
</script>
