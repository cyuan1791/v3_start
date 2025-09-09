<script setup lang="ts">
import { ref } from 'vue'


defineProps<{ msg: string }>()

declare global {
  interface Window {
    asoneData: string;
  }
}
let data = ref<any[]>(JSON.parse(atob(window.asoneData)));
console.log(data);

const count = ref(0)
</script>

<template>
  <h1>WebAsOne + {{ msg }}</h1>

  <div class="card p-4">
    <button class="btn btn-primary " type="button" @click="count++">count is {{ count }}</button>

  </div>
  <div class="p-3">
    <ul>
      <li v-for="item in data">
        <span> SlideType : {{ item.SlideType }}, title : {{ item.title }}, date : {{ item.date }}, image : {{ item.image
          }} ... </span>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>

