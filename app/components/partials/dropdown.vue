<template>
  <div>
    <no-ssr>
      <escape-handler @escapePressed="close" />
    </no-ssr>
    <button
      @click="isOpen = !isOpen"
      class="relative z-10 block font-medium px-4 py-1 md:p-2 lg:px-4"
    >
      Family
    </button>
    <button
      v-if="isOpen"
      @click="isOpen = false"
      tabindex="-1"
      class="fixed inset-0 h-full w-full bg-black opacity-25 cursor-default"
    ></button>
    <div v-if="isOpen" class="absolute right-0 mt-2 py-2 bg-gray-100 rounded-lg shadow-xl">
      <nuxt-link
        class="block px-4 py-2 hover:bg-blue-500 hover:text-white"
        v-for="(page, index) in pages"
        :key="index"
        :to="`/${page.slug}`"
        >{{ page.title }}</nuxt-link
      >
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import EscapeHandler from '@/components/partials/escapeHandler.vue';

@Component({
  components: {
    EscapeHandler,
  },
})
export default class Dropdown extends Vue {
  isOpen = false;

  get pages(): Page[] {
    return this.$store.state.pages;
  }

  close(): void {
    this.isOpen = false;
  }
}
</script>
