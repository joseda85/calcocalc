<template>
  <div id="app">
    <div id="input">{{ output }}</div>
    <div id="result">{{ result }}</div>
    <div id="keys">
      <div class="row">
        <key label="7" write="7" shortkey="7" type="number"></key>
        <key label="8" write="8" shortkey="8" type="number"></key>
        <key label="9" write="9" shortkey="9" type="number"></key>
        <key label="/" write="/" shortkey="/" type="operation"></key>
      </div>
      <div class="row">
        <key label="4" write="4" shortkey="4" type="number"></key>
        <key label="5" write="5" shortkey="5" type="number"></key>
        <key label="6" write="6" shortkey="6" type="number"></key>
        <key label="x" output="x" write="*" shortkey="*" type="operation"></key>
      </div>
      <div class="row">
        <key label="1" write="1" shortkey="1" type="number"></key>
        <key label="2" write="2" shortkey="2" type="number"></key>
        <key label="3" write="3" shortkey="3" type="number"></key>
        <key label="-" write="-" shortkey="-" type="operation"></key>
      </div>
      <div class="row">
        <key label="0" write="0" shortkey="0" type="number"></key>
        <key label="." write="." shortkey="." type="special"></key>
        <action-key label="DEL" action="del()" type="special"></action-key>
        <key label="+" write="+" shortkey="+" type="operation"></key>
      </div>
    </div>
  </div>
</template>

<script>
import Key from './components/Key.vue'
import ActionKey from './components/ActionKey.vue'

  export default {
    name: 'app',
    components: { Key, ActionKey },

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

  #input, #result {
    width: 90%;
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

  .key:hover {
    background-color: black;
    color: white;
    font-weight: bold;
    cursor: pointer;
  }

  @media (max-height: 350px) {
    .key {
      font-size: 1.5em ;
    }
  }
</style>
