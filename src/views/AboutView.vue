<template>
  <main-layout>
    <div class="about">
      <h1>This is an about page</h1>
    </div>
  </main-layout>
</template>

<script>
import MainLayout from '@/components/MainLayout.vue'

export default {
  name: 'AboutView',
  components: {
    MainLayout
  }
}
</script>

<style scoped>
.about {
  padding: 20px;
}
</style>
