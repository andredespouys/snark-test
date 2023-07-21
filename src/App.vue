<script>
import ResizableImage from './components/ResizableImage.vue';
import Commands from './components/Commands.vue';
import SecurityCheck from './components/SecurityCheck.vue';

export default {
  components: {
    ResizableImage,
    Commands,
    SecurityCheck,
  },
};
</script>

<template>
  <div class="hero">
    <h1 class="title">Snark Factory Exercises</h1>
    <h2 style="font-size: 1.5rem;">Made with</h2>
    <div class="logos">
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <a style="color: blue; text-decoration: underline;" href="https://github.com/andredespouys/snark-test">See Github</a>
  </div>
  <ResizableImage />
  <Commands/>
  <SecurityCheck/>
</template>

<style scoped>
.hero{
  margin: 4rem 3rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
}
.title{
  font-size: 3rem;
  text-align: center;
}
.logos{
  display: flex;
}
.logo {
  width: 150px;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
