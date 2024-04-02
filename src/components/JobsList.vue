<template>
  <div class="jobs-list">
    <ul>
      <li v-for="job in jobs" :key="jobs.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="ssolary">
          <p>{{ job.salary }} $ dollar</p>
        </div>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Maxime, neque!</p>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { defineProps, PropType } from 'vue'
import Job from '@/types/Job'
const props = defineProps({
  jobs: {
    required: true,
    type: Array as PropType<Job[]>
  }
})
</script>

<style scoped></style>
