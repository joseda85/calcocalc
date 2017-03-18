<template>
  <div class="key" :class="type" @click="print">
    {{ label }}
  </div>
</template>

<script>
export default {
  name: 'key',
  props: ['label', 'output', 'write', 'type'],

  methods: {
    print(){
      if (this.output != undefined){
        this.$parent.output += this.output;
      }
      else {
        this.$parent.output += this.write;
      }

      this.$parent.input += this.write;
    }
  }

}
</script>

<style lang="css">

</style>
