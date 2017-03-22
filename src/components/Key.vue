<template>
  <div class="key" :class="type" @click="launchAction">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'key',
  props: ['action', 'output', 'write', 'make', 'type'],

  methods: {
    launchAction(){
      eval('this.' + this.action + '()');
    },

    print(){
      if (this.output != undefined){
        this.$parent.output += this.output;
      }
      else {
        this.$parent.output += this.write;
      }

      this.$parent.input += this.write;
    },

    do(){
      eval('this.$parent.'+this.make);
    }
  }
}
</script>

<style lang="css">

</style>
