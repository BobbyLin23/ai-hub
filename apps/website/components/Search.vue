<script lang="ts" setup>
import { Sparkles } from 'lucide-vue-next'

const searchMode = ref<'keyword' | 'ai'>('keyword')
const searchText = ref('')

const placeholder = computed(() => {
  return searchMode.value === 'keyword'
    ? 'Search by name, keywords...'
    : 'Describe your needs, AI will recommend tools for you...'
})

// function toggleSearchMode() {
//   searchMode.value = searchMode.value === 'keyword' ? 'ai' : 'keyword'
//   searchText.value = ''
// }

async function handleSearch() {
  if (!searchText.value.trim())
    return

  if (searchMode.value === 'keyword') {
    // TODO: 实现关键词搜索
  }
  else {
    // TODO: 实现 AI 推荐搜索
  }
}
</script>

<template>
  <div class="container mb-12">
    <div class="flex justify-center">
      <div class="w-full max-w-3xl space-y-4">
        <!-- 搜索模式切换 -->
        <div class="flex justify-center gap-2">
          <Button
            :variant="searchMode === 'keyword' ? 'default' : 'outline'"
            size="sm"
            @click="() => searchMode = 'keyword'"
          >
            <Icon name="mdi:magnify" class="size-4" />
            Keyword Search
          </Button>
          <Button
            :variant="searchMode === 'ai' ? 'default' : 'outline'"
            size="sm"
            @click="() => searchMode = 'ai'"
          >
            <Sparkles class="size-4" />
            AI Recommend
          </Button>
        </div>

        <!-- 搜索框 -->
        <div class="relative">
          <Input
            v-model="searchText"
            :placeholder="placeholder"
            class="h-12 text-lg pr-24"
            @keyup.enter="handleSearch"
          />
          <Button
            class="absolute right-0 bottom-0 h-full top-0"
            :variant="searchMode === 'ai' ? 'default' : 'secondary'"
            @click="handleSearch"
          >
            <Icon
              :name="searchMode === 'keyword' ? 'mdi:magnify' : 'mdi:star-four-points'"
              class="size-4 mr-1"
            />
            {{ searchMode === 'keyword' ? 'Search' : 'Ask AI' }}
          </Button>
        </div>

        <!-- 搜索提示 -->
        <p class="text-center text-sm text-muted-foreground">
          {{ searchMode === 'keyword'
            ? 'Search by tool name, category, or keywords'
            : 'Tell AI what you want to achieve, and it will recommend the most suitable tools' }}
        </p>
      </div>
    </div>
  </div>
</template>
