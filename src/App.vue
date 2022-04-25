<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')" :class="{active: order === 'title'}">order by title</button>
        <button @click="handleClick('salary')" :class="{active: order === 'salary'}">order by salary</button>
        <button @click="handleClick('location')" :class="{active: order === 'location'}">order by location</button>
      </div>
    </header>
    <JobsList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref, toRefs } from 'vue';
import JobsList from './components/JobsList.vue'
import Job from './types/Job'
import OrderTerm from './types/OrderTerm'

export default defineComponent({
  name: 'App',
  components: { JobsList },
  setup(){
    const jobs = ref<Job[]>([
      {title: 'Q Test1', location: 's lon test1', salary: 1000, id: '1'},
      {title: 'A Test2', location: 'd lon test2', salary: 3000, id: '2'},
      {title: 'G Test3', location: 'a lon test3', salary: 2500, id: '3'},
      {title: 'B Test4', location: 'k lon test4', salary: 2000, id: '4'},
      {title: 'T Test5', location: 'o lon test5', salary: 5000, id: '5'},
    ])

    const order = ref<OrderTerm>('title')

    const handleClick = (term: OrderTerm) => {
      order.value = term
    }

    return { jobs, handleClick, order }
  },
});
</script>

<style>
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
  button.active, button:hover{
    color: #d5f0ff;
    border: 3px solid #1195c9;
    background: #1195c9;
    transition: all 0.5s
  }
</style>
