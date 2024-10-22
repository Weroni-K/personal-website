<template>
  <div id="home">
    <TextAnimation />
    <div class="title-small"><h1>Welcome!</h1></div>
    <h2>
      My name is <span class="primary"><b>Weronika</b></span
      >, I am a junior <span class="primary"><b>Full Stack Developer</b></span> based in
      <span class="primary"><b>Helsinki</b></span
      >, <span class="primary"><b>Finland</b></span
      >. Welcome to my website.
    </h2>
  </div>
</template>

<script setup>
import TextAnimation from './home-components/TextAnimation.vue'
</script>

<style scoped>
#home {
  display: flex;
  flex-direction: column;
  margin-top: 20vh;
  margin-left: 160px;
  margin-right: 320px;
}
.title-small {
  display: none;
}
</style>
