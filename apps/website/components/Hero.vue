<script setup lang="ts">
const title = ref('AI Tools Discovery Hub')
const description = ref('Your trusted guide to explore, compare and master AI tools. Find the perfect AI solutions with detailed reviews, tutorials, and expert insights.')

const features = [
  { number: '500+', label: 'AI Tools' },
  { number: '20+', label: 'Categories' },
  { number: '1000+', label: 'Reviews' },
  { number: '100+', label: 'Tutorials' },
]

const typedTitle = ref('')
const typedDescription = ref('')

onMounted(() => {
  const titleChars = title.value.split('')
  let titleIndex = 0
  const titleInterval = setInterval(() => {
    if (titleIndex < titleChars.length) {
      typedTitle.value += titleChars[titleIndex]
      titleIndex++
    }
    else {
      clearInterval(titleInterval)
      const descChars = description.value.split('')
      let descIndex = 0
      const descInterval = setInterval(() => {
        if (descIndex < descChars.length) {
          typedDescription.value += descChars[descIndex]
          descIndex++
        }
        else {
          clearInterval(descInterval)
        }
      }, 30)
    }
  }, 50)
})
</script>

<template>
  <section class="relative overflow-hidden mb-16">
    <div class="absolute inset-0 bg-gradient-to-r from-primary/10 to-secondary/10 animate-gradient" />

    <div class="container relative py-24 sm:py-32">
      <div class="flex flex-col items-center text-center space-y-8">
        <h1
          class="text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-bold tracking-tighter bg-gradient-to-r from-primary to-primary-foreground bg-clip-text text-transparent"
        >
          {{ typedTitle }}
          <span class="animate-blink">|</span>
        </h1>

        <p
          class="mt-4 text-muted-foreground max-w-[700px] text-lg sm:text-xl leading-relaxed"
        >
          {{ typedDescription }}
        </p>

        <div class="flex gap-4 mt-8">
          <Button size="lg" class="animate-bounce-slow">
            Explore Tools
          </Button>
          <Button size="lg" variant="outline">
            Submit Tool
          </Button>
        </div>

        <div class="grid grid-cols-2 md:grid-cols-4 gap-8 mt-16">
          <div
            v-for="feature in features"
            :key="feature.label"
            class="flex flex-col items-center space-y-2 group hover:scale-105 transition-transform duration-300"
          >
            <span class="text-4xl font-bold bg-gradient-to-r from-primary to-purple-500 bg-clip-text text-transparent">
              {{ feature.number }}
            </span>
            <span class="text-muted-foreground group-hover:text-primary transition-colors">
              {{ feature.label }}
            </span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style>
.animate-gradient {
  background-size: 200% 200%;
  animation: gradient 15s ease infinite;
}

.animate-blink {
  animation: blink 1s step-end infinite;
}

.animate-bounce-slow {
  animation: bounce 2s ease-in-out infinite;
}

@keyframes gradient {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

@keyframes bounce {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}
</style>
