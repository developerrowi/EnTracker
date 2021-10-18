<template>
  <div class="dashboard-container">
    <div class="dashboard-text">name: {{ name }}    <br>
      firstName: {{ fullName }}

      <button @click="btnMessage()"> Some button </button>
    </div>
  </div>
</template>









<script>
import { mapGetters } from 'vuex'

export default {
  name: 'Dashboard',
  data() {
    return {
      firstName: "Axie1",
      lastName: "Termi",
      middle: "yeah"

    };



  },
  computed: {

    name () {
      return "Rastman"
    },

    fullName() {
      return this.firstName + " " + this.middle +  " " + this.lastName  
    }

  },
methods: {
  btnMessage() {


    fetch('https://jsonplaceholder.typicode.com/todos/1')
      .then(res => res.json())
      .then(res => { 
          this.middle = res.title
      })
  }
}}
</script>









<style lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
</style>
