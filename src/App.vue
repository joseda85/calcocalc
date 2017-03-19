<template>
  <div id="app">
    <div id="top">
      <div id="screens">
        <div id="input">{{ output }}</div>
        <div id="result">{{ result }}</div>
      </div>
      <div id="clear" @click="clear">
        CE
      </div>
    </div>
    <div id="keys">
      <div class="row">
        <key label="7" action="print" write="7" type="number"></key>
        <key label="8" action="print" write="8" type="number"></key>
        <key label="9" action="print" write="9" type="number"></key>
        <key label="/" action="print" write="/" type="operation"></key>
      </div>
      <div class="row">
        <key label="4" action="print" write="4" type="number"></key>
        <key label="5" action="print" write="5" type="number"></key>
        <key label="6" action="print" write="6" type="number"></key>
        <key label="x" output="x" action="print" write="*" type="operation"></key>
      </div>
      <div class="row">
        <key label="1" action="print" write="1" type="number"></key>
        <key label="2" action="print" write="2" type="number"></key>
        <key label="3" action="print" write="3" type="number"></key>
        <key label="-" action="print" write="-" type="operation"></key>
      </div>
      <div class="row">
        <key label="0" action="print" write="0" type="number"></key>
        <key label="." action="print" write="." type="special"></key>
        <key label="DEL" action="do" make="del()" type="special"></key>
        <key label="+" action="print" write="+" type="operation"></key>
      </div>
    </div>
  </div>
</template>

<script>
import Key from './components/Key.vue'

  export default {
    name: 'app',
    components: { Key },

    data() {
      return {
        input: '',
        output: ''
      }
    },

    computed: {
      result(){
        try {
          if (this.input !== ''){
            return eval(this.input);
          }

          return '';
        } catch (e) {
          return '';
        }
      }
    },

    methods: {
      clear(){
        this.input = '';
        this.output = '';
      },

      del(){
        this.input = this.input.substring(0, this.input.length - 1);
        this.output = this.output.substring(0, this.output.length - 1);
      }
    }

  }
</script>

<style scoped>
  #app {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    height: 100%;
    border: 1px solid black;
    background-color: lightgrey;
  }

  #top {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  #screens {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: stretch;
    flex: 1;
  }

  #clear {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100px;
    flex: 0 0 100px;
    padding: 5px;
    margin: 5px;
    background-color: salmon;
    border: 1px solid black;
    border-radius: 50%;
    text-align: center;
    font-size: 2.5em;
  }

  #input, #result {
    width: 98%;
    flex: 0 0 45px;
    padding: 10px;
    margin: 10px auto;
    border: 1px solid black;
    text-align: right;
    font-size: 20px;
  }

  #input {
    background-color: lightblue;
  }

  #result {
    background-color: lightgreen;
  }

  #keys {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: stretch;
    flex-grow: 1;
  }

  div.row {
    display: flex;
    flex: 1;
  }

  .key {
    display: flex;
    justify-content: center;
    align-items: center;
    flex: 1 1 20%;
    padding:5px;
    margin: 5px;
    border: 1px solid black;
    text-align: center;
    font-size: 2.5em;
  }

  .key.number {
    background-color: darkgrey;
  }

  .key.operation {
    background-color: lightpink;
  }

  .key.special {
    background-color: lightcyan;
  }

  .key:hover, #clear:hover {
    background-color: black;
    color: white;
    font-weight: bold;
    cursor: pointer;
  }

  @media (max-height: 350px) {
    #clear {
      flex: 0 0 75px;
      height: 75px;
      padding: 2px;
      margin: 5px;
      font-size: 20px;
    }

    #input, #result {
      flex: 0 0 30px;
      padding: 5px;
      font-size: 15px;
    }

    .key {
      font-size: 1.5em ;
    }
  }
</style>
