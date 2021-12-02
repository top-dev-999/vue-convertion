<template>
    <div class='container'>
        <label>From:</label>
        <br/>
        <select class='form-select' ref='currency' @change="selectCurrency">
            <option>USD</option>
            <option>EUR</option>
        </select>
        <br/>
        <input type="number" class="form-control" @keyup="inputCurrency" >
    </div>
</template>

<script>
export default {
  name: 'ConvertionFrom',
  methods: {
      inputCurrency: function(e) {
        this.value = e.target.value;
        this.$emit('change', {currency: this.currency, value: this.value});
      },
      selectCurrency: function(e) {
          this.currency = e.target.value;
          this.$emit('change', {currency: this.currency, value: this.value});
      }
  },
  data: function() {
      return {
          currency: 'USD',
          value: 0
      }
  }
}
</script>

<style scoped>

</style>