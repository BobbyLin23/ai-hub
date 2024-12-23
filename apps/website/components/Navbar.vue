<script lang="ts" setup>
const isVisible = ref(false)

onMounted(() => {
  isVisible.value = true
})
</script>

<template>
  <Transition
    enter-from-class="opacity-0 -translate-y-4"
    enter-to-class="opacity-100 translate-y-0"
    enter-active-class="transition duration-300"
    leave-from-class="opacity-100"
    leave-to-class="opacity-0 -translate-y-4"
    leave-active-class="transition duration-300"
  >
    <header v-show="isVisible" class="sticky top-0 z-50 w-full border-b bg-background/95 backdrop-blur supports-[backdrop-filter]:bg-background/60">
      <div class="container flex h-14 items-center">
        <div class="mr-4 flex">
          <Logo />
        </div>
        <div class="flex-1 flex justify-end md:justify-center">
          <ClientOnly>
            <NavMenu />
          </ClientOnly>
        </div>
        <div class="flex items-center space-x-2">
          <ClientOnly>
            <LangToggle />
            <ModeToggle />
            <LoginButton />
          </ClientOnly>
        </div>
      </div>
    </header>
  </Transition>
</template>
