<template>
  <div class="app">
    <header>
      <div class="title">
        <div><img src="../src/assets/the-monkey.svg" alt="" /></div>
        <h1 class="title-jiji">JuniorJobs</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>

    <JobsList :jobs="jobs" :order="order" />
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import Job from '@/types/Job'
import OrderTerm from './types/OrderTerm'
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

const order = ref<OrderTerm>('title')
const handleClick = (term: OrderTerm) => {
  order.value = term
}
</script>

<style scoped>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}

.title-jiji {
  font-weight: 900;
}
</style>
