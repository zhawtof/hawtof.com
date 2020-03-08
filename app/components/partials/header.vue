<template>
  <header class="flex items-center justify-between py-4 md:py-8 h-16">
    <nuxt-link class="block mt-2 bg-white shadow-xl rounded-lg hover:bg-gray-200" to="/">
      <img class="h-16 p-2" :src="logo" alt="Logo" />
    </nuxt-link>
    <nav class="nav ml-auto">
      <ul class="flex flex-row items-center sm:mt-4 sm:pt-4 md:mt-0 md:pt-0 md:mr-4 lg:mr-8">
        <li>
          <nuxt-link to="/" class="block font-medium px-4 py-1 md:p-2 lg:px-4">
            Home
          </nuxt-link>
        </li>
        <li>
          <nuxt-link to="/blog" class="block font-medium px-4 py-1 md:p-2 lg:px-4">
            Blog
          </nuxt-link>
        </li>
        <li>
          <button class="block font-medium px-4 py-1 md:p-2 lg:px-4">
            Family
          </button>
          <div class="mt-2 py-2 bg-gray-100 rounded-lg shadow-xl">
            <nuxt-link
              class="block px-4 py-2 hover:bg-blue-500"
              v-for="(page, index) in pages"
              :key="index"
              :to="`/${page.slug}`"
              >{{ page.title }}</nuxt-link
            >
          </div>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import settings from '@/content/settings/general.json';

@Component
export default class Header extends Vue {
  get pages(): Page[] {
    return this.$store.state.pages;
  }

  logo = settings.logo;
}
</script>

<style lang="scss">
.nav {
  ul li > a {
    &.nuxt-link-active {
      color: $bluise;
      @apply font-bold;
    }
  }
}
</style>
