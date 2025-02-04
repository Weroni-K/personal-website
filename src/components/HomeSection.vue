<template>
  <div id="home">
    <div class="main">
      <div class="text">
        <TextAnimation />
        <div class="title-small"><h1>Welcome!</h1></div>
        <h2>
          My name is <span class="primary"><b>Weronika</b></span
          >, I am a junior <span class="primary"><b>Full Stack Developer</b></span> based in
          <span class="primary"><b>Helsinki</b></span
          >, <span class="primary"><b>Finland</b></span
          >.<br />
          Welcome to my website.
        </h2>
      </div>
      <img class="main-img" :src="Image1" alt="avatar" />
    </div>
  </div>
</template>

<script setup>
import TextAnimation from './home-components/TextAnimation.vue'
import Image1 from '../assets/media/image1.png'
</script>

<style scoped>
#home {
  display: flex;
  flex-direction: column;
  max-width: 1200px;
  margin-top: 20vh;
}

.main {
  width: 100%;
  display: flex;
  gap: 10px;
}

.main-img {
  max-width: 500px;
  margin-right: 80px;
  object-fit: contain;
  width: auto;
  aspect-ratio: 1;
}

.title-small {
  display: none;
}

@media (max-width: 1248px) {
  #home {
    margin-top: 0;
    text-align: center;
    margin-inline: 72px;
  }

  .main {
    flex-wrap: wrap-reverse;
    justify-content: center;
    gap: 4rem;
  }

  .main-img {
    margin: auto;
  }

  .text-animation-container {
    margin-top: 0;
  }
}

@media (max-width: 768px) {
  #home {
    margin-inline: 24px;
  }
  .main-img {
    max-width: 100%;
    width: 500px;
  }
}
</style>
