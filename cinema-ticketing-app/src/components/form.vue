<template id="">
  <div class="">
    <label for="">Standard</label>
    <br>
    <span>
      <input type="button" name="" value="-" @click="minusStandard(), hide()" class="counter-button">
      <input type="text" name="" :value="`${standard}`"  @click="hide()" class="value">
      <input type="button" name="" value="-" @click="plusStandard(), hide()" class="counter-button">
    </span>
  </div>
  <div class="">
    <label for="">Concession</label>
    <br>
    <span>
      <input type="button" name="" value="-" @click="minusConcession(), hide()" class="counter-button">
      <input type="text" name="" :value="`${concession}`"  @click="hide()" class="value">
      <input type="button" name="" value="-" @click="plusConcession(), hide()" class="counter-button">
    </span>
  </div>
  <div class="">
    <span>
      <select class="" name="" v-model="selected"  @click="hide()">
        <option value="2D">2D</option>
        <option value="3D">3D</option>
        <option value="iMax">iMax</option>
      </select>
    </span>
  </div>
  <div class="">
    <input type="button" name="" class="price" value="Price" @click="sumOfTickets()">
  </div>
  <br>
  <hr>
  <div id="breakdown" class="breakdown">
    <input type="text" name="" :value="`Total Standard: £${standardPrice}`" id="std" disabled>
    <input type="text" name="" :value="`Total concessions: £${concessionPrice}`" id="con" disabled>
    <input type="text" name="" :value="`Total additions: £${selectedPrice}`" id="adds" disabled>
    <input type="text" name="" class="discounts" :value="`Discounts applied: -£${discount}`" id="dis" disabled>
    <input type="text" name="" :value="`Total cost: £${totalPrice}`" disabled>
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
      var iMax = 1.5;

      var breakdown = document.getElementById('breakdown');

      var stdDiscounts = 0;
      var conDiscounts = 0;

      var date = new Date()
      var day = date.getDay()

      if (day === 4) {
        for(let i = 1; i <= (this.standard); i++) {
          if(i%3 === 0) {
            stdDiscounts++
          }
        }

        for(let i = 1; i <= (this.concession); i++) {
          if(i%3 === 0) {
            conDiscounts++
          }
        }

      } else {
        var w = document.getElementById("dis");
        w.style.display = "none";
      }

      breakdown.style.display = "block";

      if(this.selected === "3D") {
        temp = threeD;

        this.standardPrice = ((this.standard - (stdDiscounts*2)) * std).toFixed(2);
        this.concessionPrice = ((this.concession - (conDiscounts*2)) * con).toFixed(2);
        this.totalTickets = (this.standard + this.concession).toFixed(2);
        this.selectedPrice = (this.totalTickets * temp).toFixed(2);
        this.discount = ((stdDiscounts*2) * std) + ((conDiscounts*2) * con).toFixed(2);
        this.totalPrice = ((this.standardPrice + this.concessionPrice) + this.selectedPrice).toFixed(2);

      }else if(this.selected === "iMax") {
        temp = iMax;

        this.standardPrice = ((this.standard - (stdDiscounts*2)) * std).toFixed(2);
        this.concessionPrice = ((this.concession - (conDiscounts*2)) * con).toFixed(2);
        this.totalTickets = (this.standard + this.concession).toFixed(2);
        this.selectedPrice = (this.totalTickets * temp).toFixed(2);
        this.discount = ((stdDiscounts*2) * std) + ((conDiscounts*2) * con).toFixed(2);
        this.totalPrice = ((this.standardPrice + this.concessionPrice) + this.selectedPrice).toFixed(2);

      } else {
        temp = 0;

        this.standardPrice = ((this.standard - (stdDiscounts*2)) * std);
        this.concessionPrice = ((this.concession - (conDiscounts*2)) * con);
        this.totalTickets = (this.standard + this.concession);
        this.selectedPrice = (this.totalTickets * temp);
        this.discount = ((stdDiscounts*2) * std) + ((conDiscounts*2) * con);
        this.totalPrice = ((this.standardPrice + this.concessionPrice) + this.selectedPrice).toFixed(2);

      }
    },
    hide() {
      var a = document.getElementById('breakdown');
      a.style.display = "none";
    }
  }
}

</script>

<style scoped>

.counter-button {
  border: none;
  background-color: lightblue;
  width: 30px;
  height: 30px;
  margin: 10px;
}

.value {
  width: 30px;
  height: 30px;
}

input {
  border: none;
  text-align: center;
}

select {
  border: none;
  font-size: 1em;
}

.price {
  margin: 10px;
  background-color: lightblue;
  font-size: 1em;
  padding: 10px;
  width: 100px;
}

.breakdown {
  display: none;
}

.discounts {
  color: green;
}


</style>
