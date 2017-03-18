<template>
  <div class="key" :class="type" @click="make">
    {{ label }}
  </div>
</template>

<script>
export default {
  name: 'action-key',
  props: ['label', 'action', 'type'],

  methods: {
    make(){
      eval('this.$parent.'+this.action);
    }
  }

}
</script>

<style lang="css">

</style>
