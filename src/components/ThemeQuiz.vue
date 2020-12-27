<template>
  <div>
    <div v-if="isQuizStarted">
      <h4>{{ operandLeft }} {{ theme }} {{ operandRight }}</h4>
      <button
        @click="selectAnswer(answer)"
        v-for="(answer, index) of answers"
        :key="index"
      >
        {{ answer }}
      </button>
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
      answers: [],
      expectedAnswer: null,
    };
  },
  methods: {
    selectAnswer(answerSelected) {
      //se a resposta está errada
      if (answerSelected !== this.expectedAnswer) {
        alert("RESPOSTA ERRADA");
      }
      this.startQuiz();
    },

    startQuiz() {
      this.isQuizStarted = true;
      this.operandLeft = parseInt(Math.random() * 13);
      this.operandRight = parseInt(Math.random() * 13);
      const methods = {
        //define o tipo de opração
        "+": (a, b) => a + b,
        "-": (a, b) => a - b,
        "*": (a, b) => a * b,
        "/": (a, b) => a / b,
      };

      const methodToUse = methods[this.theme]; //operação selecionada colocada numa variável pra facilitar a manipulação
      
      this.answers = [];//impede o array de crescer a cada resposta

      this.answers.push(methodToUse(this.operandLeft, this.operandRight+1));
      this.answers.push(methodToUse(this.operandLeft+1, this.operandRight));
      this.answers.push(methodToUse(this.operandLeft+1, this.operandRight+1));
      this.answers.push(methodToUse(this.operandLeft-1, this.operandRight+1));
      this.answers.push(methodToUse(this.operandLeft-1, this.operandRight-1));
      
      const expectedAnswer = methodToUse(this.operandLeft, this.operandRight); //resposta correta
      this.answers[
        parseInt(Math.random() * this.answers.length)
      ] = expectedAnswer; //coloca a resposta certa no meio das opções
      this.expectedAnswer = expectedAnswer;
    },
  },
};
</script>

<style>
</style>