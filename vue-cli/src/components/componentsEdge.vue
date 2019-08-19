<template>
  <input ref="dateInput" v-model="date" type="date" />
</template>

<script>
import pikaday from "pikaday";
export default {
  data(){
      return{
          date:null
      }
  },
  mounted: function () {
    var picker = new pikaday({
      field: this.$refs.dateInput,
      format: 'YYYY-MM-DD'
    })

    this.$once('hook:beforeDestroy', function () {
      picker.destroy()
    })
  }
};
</script>

<style>
</style>