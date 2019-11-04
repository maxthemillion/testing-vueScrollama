<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <Scrollama :progress=true @step-enter="stepEnterHandler" @step-progress="stepProgressHandler">
      <div class="step1 section" data-step="a" v-bind:style="{fontSize:fontSize_a + 'px'}">
        <div class='flex-item'>Some arbitrary text</div>
      </div>
      <div class="step2 section" data-step="b" v-bind:style="{fontSize:fontSize_a + 'px'}">
        <div class='flex-item'>Some arbitrary text</div>
      </div>
      <div class="step3 section" data-step="c" v-bind:style="{fontSize:fontSize_a + 'px'}">...</div>
    </Scrollama>
  </div>
</template>

<script>
import "intersection-observer"; // for cross-browser support
import Scrollama from "vue-scrollama";

export default {
  name: "app",
  components: {
    Scrollama
  },
  data(){
    return {
      styles: [{}]
    }
  },
  computed: {

  },
  methods: {
    fSize: function(index){
      return this.fontSize[index]
    },
    stepEnterHandler({element, index, direction}) {
      console.log(element, index, direction);
    },
    stepProgressHandler({element, index, progress}){
      this.styles[index].fontSize = Math.max(10, progress*50)
      this.fontSize_a = Math.max(10, progress*20)
      console.log(this.fontSize[index])
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.section {
  width:99%;
  height:80vh;
  display: flex;
  align-items: center; /* Vertical center alignment */
  justify-content: center; /* Horizontal center alignment */
  border: 1px dashed black; 
  margin-bottom:20px;
}

</style>
