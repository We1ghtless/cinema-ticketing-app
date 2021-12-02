<template id="">
  <div class="">
    <span>
      <input type="button" name="" value="-" @click="minusStandard()" class="counter-button">
      <input type="text" name="" :value="`${standard}`">
      <input type="button" name="" value="-" @click="plusStandard()" class="counter-button">
    </span>
  </div>
  <div class="">
    <span>
      <input type="button" name="" value="-" @click="minusConcession()" class="counter-button">
      <input type="text" name="" :value="`${concession}`">
      <input type="button" name="" value="-" @click="plusConcession()" class="counter-button">
    </span>
  </div>
  <div class="">
    <span>
      <select class="" name="" v-model="selected">
        <option value="2D">2D</option>
        <option value="3D">3D</option>
        <option value="iMax">iMax</option>
      </select>
    </span>
  </div>
  <div class="">
    <input type="button" name="" value="Price" @click="sumOfTickets()">
  </div>
  <br>
  <hr>
  <div class="breakdown">
    <input type="text" name="" :value="`${totalPrice}`" disabled>
  </div>
  <hr>
</template>

<script type="text/javascript">

export default {

  name: 'Form',
  data() {
    return {
      standard: 0,
      standardPrice: 0,
      concession: 0,
      concessionPrice: 0,
      totalTickets: 0,
      selected: '2D',
      selectedPrice: 0,
      discount: 0,
      totalPrice: 0,
    }
  },
  methods: {
    plusStandard() {
      this.standard++
    },
    minusStandard() {
      if(this.standard > 0) {
        this.standard--
      }
    },
    plusConcession() {
      this.concession++
    },
    minusConcession() {
      if(this.concession > 0) {
        this.concession--
      }
    },
    sumOfTickets() {
      var temp = 0;

      var std = 7.9;
      var con = 5.4;

      var threeD = .9;
      // var iMax = 1.5;

      var breakdown = document.getElementById('breakdown');

      var discounts = discounts();

      breakdown.style.display = "block";

      if(this.selected === "3D") {
        temp = threeD;

        this.standardPrice = (this.standard * std).toFixed(2);
        this.concessionPrice = (this.concession * con).toFixed(2);
        this.totalTickets = (this.standard + this.concession);
        this.selectedPrice = (this.totalTickets * temp);
        this.totalPrice = (std * this.standard) + (con * this.concession) + (temp * this.totalTickets);

      }
    },
    discounts() {
      var discount = 0;
      for(let i = 0; i < (this.standard + this.concession); i++) {
        if(i%3 === 0) {
          discount++
        }
      }
      return discount
    }

  }

}

</script>

<style scoped media="screen">

.breakdown {
  display: none;
}


</style>
