<template>
    <div>
        <b-row>
            <b-col class="mx-auto" cols="12" sm="8" md="7" lg="5" >
                <b-jumbotron class="bgc">
                    
                    <template >
                        {{ cQuestion.question }}
                        </template>

                    <hr class="my-4">
                    <b-list-group @keyup.enter="saveAnsewer()" >
                        <b-list-group-item button  class="gbList" v-for="(answer , i) in answers" :key="i" @click="btn_answer=answer">{{answer}}</b-list-group-item>
                    </b-list-group>
                    <b-button class="justify_end margin-top" 
                    @click="saveAnsewer()" 
                    >next</b-button>
                </b-jumbotron>
            </b-col>
        </b-row>
    </div>
</template>
<script>

export default {
    data(){
        return{
            btn_answer:"",
        }
    },
    props:{
         cQuestion : Object,
         next: Function
    },
    computed:{
        answers(){
            let answer = [...this.cQuestion.incorrect_answers]
            answer.push(this.cQuestion.correct_answer);
            return answer;
        },
    },
    methods:{
        saveAnsewer(){
          if(this.btn_answer == this.cQuestion.correct_answer)
            this.next(1); 
          else
            this.next(0); 
        }
    }
}
</script>
