<script lang="ts" setup>
  const app = useAppConfig();
  const route = useRoute();

  useHead({
    titleTemplate: () => (route.meta?.title ? `${route.meta?.title} | Muhammad Habibullah` : app.title),
    link: [{ rel: 'icon', type: 'image/png', href: '/images/icon.jpg' }],
    meta: [
      { hid: 'robots', name: 'robots', content: 'index, follow' },
      { hid: 'viewport', name: 'viewport', content: 'width=device-width, initial-scale=1' },
      { hid: 'description', name: 'description', content: app.description },
      { hid: 'keywords', name: 'keywords', content: app.keywords },
      { hid: 'og:site_name', property: 'og:site_name', content: app.author.name },
      { hid: 'og:url', property: 'og:url', content: 'https://bob.algohaven.com' },
      { hid: 'og:description', property: 'og:description', content: app.description },
      { hid: 'og:type', property: 'og:type', content: 'website' },
      { hid: 'og:image', property: 'og:image', content: '/images/opengraph-logo.jpg' }
    ]
  });
</script>

<template>
  <Html lang="en">
    <Body class="bg-gray-600">
      <main class="flex flex-col container mx-auto sm:px-4 px-8 min-h-screen">
        <BaseHeader :menus="app.menus.header" />

        <section class="flex flex-col w-full mt-10 justify-start mb-8">
          <h2 v-if="route.meta?.title" class="title-heading-primary font-extrabold mb-12">
            {{ route.meta.title }}
          </h2>

          <div>
            <NuxtLayout>
              <NuxtPage />
            </NuxtLayout>
          </div>
        </section>

        <BaseFooter :menus="app.menus.footer" class="mt-auto" />
      </main>
    </Body>
  </Html>
</template>
