<template>
  <div>
    <div class="flex items-center justify-between">
      <div class="flex items-center">
        <slot name="title" />
      </div>
      <button
        @click="toggleAccordion()"
        class="flex items-center space-x-3"
        :aria-expanded="isOpen"
        :aria-controls="`collapse${_uid}`"
      >
        <div
          class="
            w-3
            right-0
            transform
            -translate-y-1/2
            focus:outline-none
            transition
            duration-200
          "
          :class="isOpen ? 'rotate-180' : 'rotate-0'"
        >
          <svg
            fill="none"
            stroke="currentColor"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 16 10"
            aria-hidden="true"
          >
            <path
              d="M15 1.2l-7 7-7-7"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
        </div>
      </button>
    </div>
    <div v-show="isOpen" :id="`collapse${_uid}`">
      <slot name="content" />
    </div>
  </div>
</template>
<script>
export default {
  name: "Accordion",
  data() {
    return {
      isOpen: false,
    };
  },
  methods: {
    toggleAccordion() {
      this.isOpen = !this.isOpen;
    },
  },
};
</script>
