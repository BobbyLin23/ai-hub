<script lang="ts" setup>
const categories = [
  {
    title: '工具箱',
    description: '常用在线工具集合',
    items: [
      { name: '在线工具1', url: '#' },
      { name: '在线工具2', url: '#' },
    ],
  },
  {
    title: '学习资源',
    description: '优质学习平台',
    items: [
      { name: '学习平台1', url: '#' },
      { name: '学习平台2', url: '#' },
    ],
  },
  {
    title: '工具箱',
    description: '常用在线工具集合',
    items: [
      { name: '在线工具1', url: '#' },
      { name: '在线工具2', url: '#' },
    ],
  },
  {
    title: '学习资源',
    description: '优质学习平台',
    items: [
      { name: '学习平台1', url: '#' },
      { name: '学习平台2', url: '#' },
    ],
  },
  {
    title: '工具箱',
    description: '常用在线工具集合',
    items: [
      { name: '在线工具1', url: '#' },
      { name: '在线工具2', url: '#' },
    ],
  },
  {
    title: '学习资源',
    description: '优质学习平台',
    items: [
      { name: '学习平台1', url: '#' },
      { name: '学习平台2', url: '#' },
    ],
  },
  {
    title: '工具箱',
    description: '常用在线工具集合',
    items: [
      { name: '在线工具1', url: '#' },
      { name: '在线工具2', url: '#' },
    ],
  },
  {
    title: '学习资源',
    description: '优质学习平台',
    items: [
      { name: '学习平台1', url: '#' },
      { name: '学习平台2', url: '#' },
    ],
  },
  {
    title: '工具箱',
    description: '常用在线工具集合',
    items: [
      { name: '在线工具1', url: '#' },
      { name: '在线工具2', url: '#' },
    ],
  },
  {
    title: '学习资源',
    description: '优质学习平台',
    items: [
      { name: '学习平台1', url: '#' },
      { name: '学习平台2', url: '#' },
    ],
  },
]
</script>

<template>
  <div class="container pb-16">
    <div class="grid gap-6 md:grid-cols-2 lg:grid-cols-3">
      <Card v-for="category in categories" :key="category.title">
        <CardHeader>
          <CardTitle>{{ category.title }}</CardTitle>
          <CardDescription>{{ category.description }}</CardDescription>
        </CardHeader>
        <div class="p-6 pt-0">
          <ul class="space-y-2">
            <li v-for="item in category.items" :key="item.name">
              <a
                :href="item.url"
                class="text-muted-foreground hover:text-primary transition-colors"
              >
                {{ item.name }}
              </a>
            </li>
          </ul>
        </div>
      </Card>
    </div>
  </div>
</template>
