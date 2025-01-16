<template>
  <div class="layout">
    <div class="menu-bar">
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </div>
    <div class="main-content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MainLayout'
}
</script>

<style scoped>
.menu-bar {
  background-color: rgba(75, 98, 97, 0.896);
  padding: 15px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  height: 30px;
}

.main-content {
  padding-top: 60px;
}

.menu-bar a {
  color: antiquewhite;
  text-decoration: none;
  padding: 8px 15px;
  border-radius: 5px;
}

.menu-bar a:hover {
  background-color: rgba(95, 118, 117, 0.896);
}
</style> 