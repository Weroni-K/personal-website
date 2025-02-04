<template>
  <div id="home">
    <div class="main" v-if="isMobile">
      <div class="text">
        <TextAnimation />
        <div class="title-small"><h1>Welcome!</h1></div>
        <img class="main-img" :src="Image1" alt="main-img" />
        <h2>
          My name is <span class="primary"><b>Weronika</b></span
          >, I am a junior <span class="primary"><b>Full Stack Developer</b></span> based in
          <span class="primary"><b>Helsinki</b></span
          >, <span class="primary"><b>Finland</b></span
          >.<br />
          Welcome to my website.
        </h2>
      </div>
    </div>
    <div class="main" v-else>
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
      <img class="main-img" :src="Image1" alt="main-img" />
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import TextAnimation from './home-components/TextAnimation.vue'
import Image1 from '../assets/media/image1.png'

const isMobile = ref(false)

function checkScreenSize() {
  isMobile.value = window.innerWidth <= 768
}

onMounted(() => {
  checkScreenSize()
  window.addEventListener('resize', checkScreenSize)
})
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
  align-items: center;
  gap: 10px;
}

.main-img {
  max-width: 500px;
  margin-right: 80px;
  object-fit: contain;
  width: auto;
  height: auto;
}

.title-small {
  display: none;
}

@media (max-width: 1248px) {
  #home {
    margin-top: 10rem;
    text-align: center;
    margin-inline: 72px;
  }
  .main {
    justify-content: center;
    gap: 2rem;
  }
  .text {
    width: 50%;
  }
  .main-img {
    width: 50%;
    margin: auto;
    max-width: 400px;
  }
  .text-animation-container {
    margin-top: 0;
  }
}

@media (max-width: 768px) {
  #home {
    margin-inline: 24px;
    margin-top: 6rem;
  }
  .text {
    width: 100%;
  }
  .main-img {
    max-width: 350px;
    width: 100%;
    margin-bottom: 1rem;
  }
  .title-small {
    display: flex;
    justify-content: center;
    margin-bottom: -2rem;
    h1 {
      font-size: 38px;
    }
  }
}
</style>
