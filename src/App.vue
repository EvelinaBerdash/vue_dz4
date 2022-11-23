<template>
  <div id="app">
    <HomeView v-on:add="add" v-bind:categories="categories" v-bind:list='paymentsList'/>
  </div>
</template>

<script>
import HomeView from './views/HomeView.vue'
import { mapMutations } from 'vuex'


export default {
  name: 'App',
  components: { HomeView }, 
  data() {
    return {
      categories: [
       'food',
       'transport',
      ],
      paymentsList: [
      { id: 1, category: 'food', date: '12.09.2022 20:27', count: 1582 },
      ]      
    }
  },
  methods: {
    add(formData) {
      formData.date = new Date().toLocaleDateString('en-us', { weekday:"long", year:"numeric", month:"short", day:"numeric"}),
      this.paymentsList.push(Object.assign({}, formData))
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
