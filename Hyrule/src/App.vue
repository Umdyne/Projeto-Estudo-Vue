<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="Site Logo">
        <h1>Hyrule Jobs :D</h1>
      </div>
      <div class="order">
      <button @click="handleClick('title')">order by title</button>
      <button @click="handleClick('salary')">order by salary</button>
      <button @click="handleClick('location')">order by location</button>
    </div>
    </header>
    
    
    <JobListVue :jobs ="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent , reactive , toRefs , ref} from 'vue'
import JobListVue from './components/JobList.vue'
import Job from './types/Job'
import OrderTerm from './types/OrderTerm'


export default defineComponent({
  name: 'App',
  components: { JobListVue },
  setup(){

    const jobs = ref<Job[]>([
      {title : 'Farm Worker', location : 'Lon Lon Runch', salary : 5000, id : '1',},
      {title : 'Fisher', location : 'River', salary : 60000, id : '2',},
      {title : 'Guard', location : 'Castle', salary : 50000, id : '3',},
      
    ])
    const order = ref<OrderTerm>('title')
    const handleClick = (term: OrderTerm) => {
      order.value = term
    }
    return {jobs , handleClick , order}
  },
  methods: {
    changeName(name : string){
      this.name = name
      return name
    },
    changeAge(age : string | number){
      this.age = age
      return age
    }
  }
})
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
  header .title{
    display: flex;
    justify-content: center;
  }
  header img {
    width: 60px;
    margin-right: 20px;
  }
  header h1 {
    font-size: 3em;
  }
</style>