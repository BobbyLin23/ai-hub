<script setup lang="ts">
import { Languages } from 'lucide-vue-next'

const languages = [
  { code: 'zh', label: '中文' },
  { code: 'en', label: 'English' },
]

const currentLang = ref('zh')

function switchLanguage(lang: string) {
  currentLang.value = lang
}
</script>

<template>
  <DropdownMenu>
    <DropdownMenuTrigger as-child>
      <Button variant="ghost" size="icon">
        <Languages class="h-5 w-5" />
        <span class="sr-only">Switch Language</span>
      </Button>
    </DropdownMenuTrigger>
    <DropdownMenuContent align="end">
      <DropdownMenuItem
        v-for="lang in languages"
        :key="lang.code"
        @click="switchLanguage(lang.code)"
      >
        {{ lang.label }}
      </DropdownMenuItem>
    </DropdownMenuContent>
  </DropdownMenu>
</template>
