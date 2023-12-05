<script setup>
import { ref } from 'vue'
const wps = ref([
  { name: 'work package foo', path: '/work-package-foo' },
  { name: 'work package bar', path: '/work-package-bar' },
])

const toWp = ({ path }) => {
  window.open(path, '_blank')
}
</script>

<template>
  <main>
    <div class="wp-list">
      <div v-for="item in wps" class="wp-list-item" @click="toWp(item)">{{ item.name }}</div>
    </div>
  </main>
</template>
<style>
.wp-list {
  display: flex;
  padding: 32px;

}
.wp-list-item {
  width: 200px;
  height: 100px;
  border: 1px solid #ccc;
  margin-left: 16px;
  text-align: center;
  line-height: 100px;

}
.wp-list-item:hover {
  cursor: pointer;
  color: blue;
}
</style>
