<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <AddButton :onClick="popupToggle"></AddButton>
    <List v-bind:list="costsList">
      <template v-slot:head>
        <h2>Мои расходы</h2>
      </template>
      <template v-slot:footer>
        <h2>Good bye</h2>
      </template>
    </List>
    <Form v-if="isPopupActive" :onAdd='onAdd'></Form>
  </div>
</template>

<script>
import AddButton from './components/AddButton.vue'
import Form from './components/Form.vue'
import List from './components/List.vue'
import { mapMutations } from 'vuex'


export default {
  name: 'App',
  components: { AddButton, Form, List },
  data() {
    return {
      costsList: [],
      isPopupActive: false,
      nextId: 4,
    }
  },
  methods: {
    fetchData() {
      return [
        { id: 1, date: '12.09.2022', category: 'food', value: 1582 },
        { id: 2, date: '15.09.2022', category: 'transport', value: 245 },
        { id: 3, date: '20.09.2022', category: 'healthcare', value: 780 },
      ]
    },
    popupToggle() {
      this.isPopupActive = !this.isPopupActive
    },
    onAdd(data) {
      // let nextId = costsList.map(function(cost),
      this.costsList.push({
        id: this.nextId++,
        date: data.date,
        category: data.category,
        value: data.value
      }),
        mapMutations({
          updatePayments: 'setPaymentsListData'
        })
      //console.log('child component said add', data)
    }
  },
  created() {
    this.setPaymentsListData(this.updatePayments)
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
