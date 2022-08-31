<template>
  <div class="relative">
    <button
      @click="openDropdown"
      @blur="isDropdownOpen = false"
      class="bg-gradient-to-r from-blue-600 to-blue-400 text-white font-medium uppercase tracking-widest rounded-sm py-3 px-4 drop-shadow-2xl w-full"
    >
      <slot name="title"></slot>
    </button>

    <transition name="slide-fade">
      <ul
        v-if="isDropdownOpen"
        class="absolute left-0 right-0 mb-4 bg-white divide-y rounded-sm shadow-lg overflow-hidden"
      >
        <li
          v-for="dropdownValue in dropdownValues"
          @click="selectItem"
          class="px-4 py-3 transition-colors duration-300 hover:bg-gray-200 cursor-pointer"
        >
          {{ dropdownValue }}
        </li>
      </ul>
    </transition>
  </div>
</template>

<script>
export default {
  props: {
    dropdownValues: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      isDropdownOpen: false,
    };
  },
  methods: {
    openDropdown() {
      this.isDropdownOpen = !this.isDropdownOpen;
    },
    selectItem() {
      this.isDropdownOpen = false;
    },
  },
};
</script>

<style scoped>
/* dropdown animation */
.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.5s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateY(15px);

  opacity: 0;
}
</style>
