<template>
  <header class="flex items-center justify-between py-4 md:py-8 h-16">
    <nuxt-link class="block mt-4 bg-white shadow-xl rounded-lg hover:bg-gray-200" to="/">
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
        <li class="relative">
          <no-ssr placeholder="loading...">
            <menu-dropdown></menu-dropdown>
          </no-ssr>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import settings from '@/content/settings/general.json';

import MenuDropdown from '@/components/partials/dropdown.vue';

@Component({
  components: {
    MenuDropdown,
  },
})
export default class Header extends Vue {
  logo = settings.logo;

  get pages(): Page[] {
    return this.$store.state.pages;
  }
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
