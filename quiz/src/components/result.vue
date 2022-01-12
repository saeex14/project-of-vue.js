<template>
  <div ref="sss">
    <b-row>
      <b-col sm="5" offset="4">
        <b-jumbotron class="bgc">
          <template> Your correct answer : {{this.correct}} / 10 </template>
          <b-button class="justify_end margin-top" @click="reset"
            >Again</b-button
          >
        </b-jumbotron>
      </b-col>
    </b-row>
  </div>
</template>
<script>
export default {
    data(){
        return{
            
        }
    },
    props: {
    correct: Number,
    reset: Function,
  },  
};
</script>
