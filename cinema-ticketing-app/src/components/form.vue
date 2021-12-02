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
      selected: '',
      selectedPrice: 0,
      totalPrice: 0,
      totalTickets: 0
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
  }

}

</script>
