<template>
  <div class="bgi">
    <div v-if="this.index != 10">
      <Header :index="this.index + 1" />
      <Content 
      :cQuestion ="questionList[index]" 
      :next="next" v-if="questionList.length" 
       />  
    </div>
    <div v-else>
      <Result 
      :correct="this.correct" 
      :reset="this.reset" />
    </div>
  </div>
</template>

<script>
import Header from "./components/header.vue";
import Content from "./components/content.vue";
import Result from "./components/result.vue";

export default {
  name: "App",
  components: {
    Content,
    Result,
    Header,
  },
  data() {
    return {
      questionList: [],
      index: 0 ,
      correct: 0,
    };
  },
  methods:{
    next(e){
      if(this.index < 10)
         this.index++;
        this.correct += e;
        console.log(this.correct,e )
    },
    reset(){
      this.index = 0;
      this.correct = 0
    }
  },
  mounted() {
    fetch("https://opentdb.com/api.php?amount=10&category=25&type=multiple", {
      method: "get",
    })
      .then((respons) => {
        return respons.json();
      })
      .then((result) => {
        this.questionList = result.results;
      });
  },
};
</script>