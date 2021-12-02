<template>
    <div class='container'>
        <label>To:</label>
        <br/>
        <select class='form-select' ref='currency' @change="selectCurrency">
            <option>USD</option>
            <option>EUR</option>
        </select>
        <br/>
        <input type="number" class="form-control" v-bind:value="value">
    </div>
</template>

<script>
export default {
  name: 'ConvertionTo',
  props: ['value'],
  data: function() {
      return {
          currency: 'USD',
      }
  },
  methods: {
      selectCurrency: function(e) {
          this.currency = e.target.value;
          this.$emit('change', {currency: this.currency});
      }
  },
}
</script>

<style scoped>

</style>