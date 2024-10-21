<template>
  <header class="navbar">
    <input id="menu-toggle" type="checkbox" v-model="isMenuOpen" />
    <label class="menu-button-container" for="menu-toggle">
      <div class="menu-button"></div>
    </label>
    <ul class="menu">
      <li><RouterLink to="#home">Home</RouterLink></li>
      <li><RouterLink to="#about">About</RouterLink></li>
      <li><RouterLink to="#projects">Projects</RouterLink></li>
      <li><RouterLink to="#contact">Contact</RouterLink></li>
      <li>
        <a href="https://github.com/Weroni-K" target="_blank">
          <GitHubIcon />
        </a>
      </li>

      <li>
        <a href="https://www.linkedin.com/in/weronika-kirchner/" target="_blank">
          <LinkedInIcon />
        </a>
      </li>
    </ul>
    <div class="toggle-theme">
      <label :class="['theme-switch', { dark: isDarkMode }]">
        <input type="checkbox" :checked="isDarkMode" @change="toggleDarkMode" />
        <span class="slider round"></span>
      </label>
    </div>
  </header>
  <main>
    <section id="home" data-aos="fade-left" data-aos-duration="1000">
      <Home />
    </section>
    <section id="about" data-aos="fade-right" data-aos-duration="1200">
      <About />
    </section>
    <section id="projects" data-aos="fade-left" data-aos-duration="1200">
      <Projects />
    </section>
    <section id="contact" data-aos="fade-up-left" data-aos-duration="1200">
      <Contact />
    </section>
  </main>
  <ScrollToTopButton />
  <footer>
    <p>Copyright&copy; 2024 Weroni-K All Rights Reserved.</p>
  </footer>
</template>

<script setup>
import { RouterLink } from 'vue-router'
import Home from './components/HomeSection.vue'
import About from './components/AboutSection.vue'
import Projects from './components/ProjectsSection.vue'
import Contact from './components/ContactSection.vue'
import { ref, watch } from 'vue'
import ScrollToTopButton from './components/ScrollToTopButton.vue'
import GitHubIcon from './components/main-manu-components/GitHubIcon.vue'
import LinkedInIcon from './components/main-manu-components/LinkedInIcon.vue'

const isDarkMode = ref(false)

const toggleDarkMode = () => {
  isDarkMode.value = !isDarkMode.value
  document.documentElement.classList.toggle('dark-theme', isDarkMode.value)
}

// load dark mode preference from localStorage
if (localStorage.getItem('dark-mode') === 'true') {
  isDarkMode.value = true
  document.documentElement.classList.add('dark-theme')
}

// save dark mode preference to localStorage
watch(isDarkMode, (newValue) => {
  localStorage.setItem('dark-mode', newValue)
})

const isMenuOpen = ref(false)
</script>
