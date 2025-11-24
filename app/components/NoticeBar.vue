<script setup lang="ts">
const props = defineProps<{
  message?: string
}>()

const isVisible = ref(!!props.message)

onMounted(() => {
  if (isVisible.value) {
    setTimeout(() => {
      isVisible.value = false
    }, 60000) // 60 seconds
  }
})
</script>

<template>
  <Transition
    enter-active-class="transition-all duration-300 ease-out"
    enter-from-class="opacity-0 -translate-y-4"
    enter-to-class="opacity-100 translate-y-0"
    leave-active-class="transition-all duration-300 ease-in"
    leave-from-class="opacity-100 translate-y-0"
    leave-to-class="opacity-0 -translate-y-4"
  >
    <div v-if="isVisible && message" class="w-full bg-primary-50 dark:bg-primary-900/30 border-b border-primary-100 dark:border-primary-800/50">
      <div class="container mx-auto px-4 py-3">
        <div class="flex items-center justify-center text-sm font-medium text-primary-700 dark:text-primary-200">
          <Icon name="ph:megaphone-simple-fill" class="mr-2 text-lg" />
          <span>{{ message }}</span>
        </div>
      </div>
    </div>
  </Transition>
</template>
