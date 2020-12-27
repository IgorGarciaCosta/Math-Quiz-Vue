<template>
  <div>
      <div v-if="isQuizStarted">
          <h4>{{operandLeft}} {{theme}} {{operandRight}}</h4>
          <button @click="selectAnswer(answers)" v-for="answer of answers" :key="answer">{{answer}}</button>
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
      const methods = {//define o tipo de opração
        '+':(a, b)=>a+b,
        '-':(a, b)=>a-b,
        '*':(a, b)=>a*b,
        '/':(a, b)=>a/b,
      }

      const methodToUse = methods[this.theme];//operação selecionada colocada numa variável pra facilitar a manipulação
      for(let i=0; i<5; i++){//número de opções
          const answer = methodToUse(//define valorer aleatórios pra opções
            parseInt(Math.random()*3), 
            parseInt(Math.random()*3),
          );  
          this.answers.push(answer)//coloca dentro do array de opções
      }
      const expectedAnswer = methodToUse(this.operandLeft, this.operandRight);//resposta correta
      this.answers[parseInt(Math.random()*this.answers.length)] = expectedAnswer;//coloca a resposta certa no meio das opções
    },
  },
};
</script>

<style>
</style>