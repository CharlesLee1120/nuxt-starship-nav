<script setup lang="ts">
const show = ref(false)

const checkScroll = () => {
  show.value = window.scrollY > 300
}

const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  })
}

onMounted(() => {
  window.addEventListener('scroll', checkScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', checkScroll)
})
</script>

<template>
  <Transition name="fade">
    <button
      v-if="show"
      @click="scrollToTop"
      class="fixed bottom-10 right-10 z-50 p-4 rounded-full bg-white/90 dark:bg-dark-surface/90 backdrop-blur-xl border border-slate-200 dark:border-dark-border shadow-xl hover:shadow-2xl text-primary-600 dark:text-primary-400 hover:scale-110 active:scale-95 transition-all duration-300 group"
      aria-label="Back to top"
    >
      <Icon name="ph:arrow-up-bold" class="text-2xl group-hover:-translate-y-1 transition-transform duration-300" />
    </button>
  </Transition>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(20px);
}
</style>
