<template>
    <div class="convertion-container">
      <div class="convertion">
        <div class="from">
          <convertion-from @change="getFromValue"></convertion-from>
        </div>
        <div class="to">
          <convertion-to @change="getFromTo" v-bind:value="toValue"></convertion-to>
        </div>
      </div>

      <button class="btn btn-success btn-lg" @click="convert">Convert</button>
    </div>
</template>

<script>
import ConvertionFrom from './ConvertionFrom.vue';
import ConvertionTo from './ConvertionTo.vue';
import { rate } from '../helper';
export default {
  name: 'Convertion',
  components: {
    ConvertionFrom,
    ConvertionTo
  },
  data: function() {
    return {
      fromValue: 0,
      fromCurrency: 'USD',
      toCurrency: 'USD',
      toValue: 0
    }
  },
  methods: {
    getFromValue: function(obj) {
      this.fromValue = obj.value;
      this.fromCurrency = obj.currency;
    },
    getFromTo: function(obj) {
      this.toCurrency = obj.currency
    },
    convert: function() {
      this.toValue = this.fromValue * (rate[this.fromCurrency] / rate[this.toCurrency]);
      console.log(this.toValue);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .convertion-container {
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 20px;
  }
  .convertion {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
  }
</style>
