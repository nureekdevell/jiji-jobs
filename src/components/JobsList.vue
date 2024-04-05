<template>
  <div class="job-list">
    <p>Order By {{ order }}</p>
    <transition-group name="list" tag="ul">
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <img src="../assets/dollar-16.svg" alt="" />
          <p>{{ job.salary }} dollar</p>
        </div>
        <div class="description">
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Maxime, neque!</p>
        </div>
      </li>
    </transition-group>
  </div>
</template>

<script setup lang="ts">
import { computed, defineProps } from 'vue'
import type Job from '@/types/Job'
import type OrderTerm from '@/types/OrderTerm'

const props = defineProps<{
  jobs: Job[]
  order: OrderTerm
}>()

// const props = defineProps({
//   jobs: {
//     required: true,
//     type: Array as PropType<Job[]>
//   },
//   order: {
//     required: true,
//     type: String as PropType<OrderTerm>
//   }
// })

const orderedJobs = computed(() => {
  const jobs = props.jobs
  const orders = jobs.sort((a, b) => {
    return a[props.order] > b[props.order] ? 1 : -1
  })

  return orders
})
</script>

<style scoped>
.job-list {
  max-width: 960px;
  margin: 40px auto;
}
.job-list ul {
  padding: 0;
}
.job-list li {
  list-style-type: none;
  background: white;
  padding: 16px;
  margin: 16px 0;
  border-radius: 4px;
}
.job-list h2 {
  margin: 0 0 10px;
  text-transform: capitalize;
}
.salary {
  display: flex;
}
.salary img {
  width: 30px;
}
.salary p {
  color: #17bf66;
  font-weight: bold;
  margin: 10px 4px;
}

.list-move, /* apply transition to moving elements */
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
.list-leave-active {
  position: absolute;
}
</style>
