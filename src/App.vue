<template>
  <div class="app">
    <JobsList :jobs="jobs" />
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import Job from '@/types/Job'
import JobsList from './components/JobsList.vue'

const jobs = ref<Job[]>([
  {
    title: 'Nurjakhon',
    location: 'Tashkent',
    salary: 30000,
    id: '1'
  },
  {
    title: 'Jakhon',
    location: 'Parkent',
    salary: 10000,
    id: '2'
  },
  {
    title: 'Khon',
    location: 'Tomchi',
    salary: 2000,
    id: '3'
  }
])
</script>

<style scoped></style>
