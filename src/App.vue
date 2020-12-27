<template>
  <!-- Aqui serão chamados os diferentes components -->
  <div id="app">
    <h1>Quiz App</h1>
    <ThemeQuiz @onBack="clearTheme" v-if="theme" :theme="theme" />
    <ThemeSelector v-if="!theme" @changeTheme="changeTheme" />
    <!--v-if faz o themeSelector só aparecer qnd  tem a não for definido-->
  </div>
</template>

<script>
import ThemeSelector from "./components/ThemeSelector.vue";
import ThemeQuiz from "./components/ThemeQuiz.vue";

export default {
  name: "App",
  data() {
    return {
      theme: null,
    };
  },
  methods: {
    changeTheme(theme) {
      this.theme = theme;
    },
    clearTheme() {
      this.theme = null;
    },
  },

  components: {
    ThemeSelector,
    ThemeQuiz,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Josefin+Sans&display=swap");
#app {
  font-family: "Josefin Sans", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 24px;
}

button {
  font-family: "Josefin Sans", sans-serif;
  color: black;
  font-weight: 500;
  padding: 10px;
  width: 170px;
  height: 80px;
  margin-right: 10px;
  background-color: #ffae19;
  color: white;
  font-size: 24px;
  cursor: pointer;
  vertical-align: top;
  border-radius: 5px;
  box-shadow: 10px 8px 15px rgba(0, 0, 0, 0.4);
  transition: all 0.3s ease 0s;
}

button:hover {
  background-color: #64ca64;
  box-shadow: 0px 15px 20px rgba(46, 229, 157, 0.4);
  transform: translateY(-7px);
}
</style>
