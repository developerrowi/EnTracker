<template>
  <div class="dashboard-container">
    <el-row :gutter="20">
       <el-col :span="12" :offset="6">
         <div class="grid-content bg-purple">
          <h1> Round {{round}} </h1>
          <h3> ENERGY USED </h3>
         </div>
         <div class="grid-content bg-purple">
        <h1> {{energy}} </h1> 
         </div>
         <div class="grid-content bg-purple p-3">
          <el-button type="danger" icon="el-icon-minus" circle @click="minusEnergy()"></el-button> 
          <el-button type="success" icon="el-icon-plus" circle @click="addEnergy()"></el-button> 
         </div>
         <div class="grid-content bg-purple p-3">
          <el-button type="primary" icon="el-icon-edit" @click="endTurn()">END TURN</el-button>
         </div> 
         <div class="grid-content bg-purple p-3">
          <el-button type="danger" icon="el-icon-share" size="mini" @click="resetBtn()">RESET </el-button>
         </div> 
        </el-col>
    </el-row>
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
      middle: "yeah",
      energy: 3,
      energyUsed: 0,
      energyDestroyed: 0,
      energyGained: 0,
      cardNumber: 6,
      zeroEnergyCardUse: 0,
      round: 1

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
  mounted() {
    window.addEventListener("keypress", e => {
      let keyCode = String.fromCharCode(e.keyCode)
      if (keyCode == "a") {
        this.minusEnergy()
      } 
		console.log(String.fromCharCode(e.keyCode));
	});
  },
methods: {
  btnMessage() {


    fetch('https://jsonplaceholder.typicode.com/todos/1')
      .then(res => res.json())
      .then(res => { 
          this.middle = res.title
      })
  },

  addEnergy() {
    this.restrictGreater10()
    this.energy = this.energy + 1;
  },
  minusEnergy() {
    this.restrictLess0()
    this.energy = this.energy - 1;
  },
  endTurn() {
    if (this.energy >= 9) {
      this.energy = 10
    } else {
      this.energy = this.energy + 2 
    }
      this.round = this.round + 1
      
    // return this.restrictGreater10() ? null : this.energy = this.energy + 2 
    

    // this.cardNumber = this.cardNumber + 3
    // this.energyUsed = 0
    // this.energyDestroyed = 0
    // this.energyGained = 0
    // this.zeroEnergyCardUse = 0
  },
    resetBtn() {
    this.energy = 3
    this.round = 1

  },
  restrictGreater10() {
    if (this.energy >= 9) {
      this.energy = 10
      return true
    }
      return false
  },
  restrictLess0() {
    if (this.energy <= 0) {
      exit;
    }
  }
  // useEnergy() {
  //   this.restrictLess0()
  //   this.energyUsed = this.energyUsed + 1
  //   this.energy = this.energy - 1
  //   this.cardNumber = this.cardNumber - 1
  // },
  // gainEnergy() {
  //   this.restrictGreater10()
  //   this.energyGained = this.energyGained + 1
  //   this.energy = this.energy + 1
  // },
  // desEnergy() {
  //   this.restrictLess0()

  //   this.energyDestroyed = this.energyDestroyed + 1
  //   this.energy = this.energy - 1
  // },
  // noEnergyCardUse() {
  //   if (this.cardNumber <= 0) {
  //     exit;
  //   } 
  //   this.cardNumber = this.cardNumber - 1
  //   this.zeroEnergyCardUse = this.zeroEnergyCardUse + 1
  // },
}}
</script>









<style lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px;
    text-align: center;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
</style>
