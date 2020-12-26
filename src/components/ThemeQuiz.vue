<template>
  <div>
      <div v-if="isQuizStarted">
          <h4>{{operandLeft}} {{theme}} {{operandRight}}</h4>
          <button v-for="answer of answers" :key="answer">{{answer}}</button>
      </div>
      
      <div v-if="!isQuizStarted">
          <button @click="startQuiz">Start</button>
          
      </div>
      <button @click="$emit('onBack')">Voltar</button>
  </div>
</template>

<script>
export default {
  props: ["theme"],
  data() {
    return {
      isQuizStarted: false,
      operandLeft: null,
      operandRight: null,
      answers:[],
    };
  },
  methods: {
    startQuiz() {
      this.isQuizStarted = true;
      this.operandLeft = parseInt(Math.random() * 13);
      this.operandRight = parseInt(Math.random() * 13);
        for(let i=0; i<5; i++){
            const answer = this.operandLeft*parseInt(Math.random()*3)+
                this.operandRight*parseInt(Math.random()*3);
            this.answers.push(answer);
        }
    },
  },
};
</script>

<style>
</style>