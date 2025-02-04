<template>
  <header :class="['navbar', { sticky: isSticky, 'menu-open': isMenuOpen }]">
    <div class="navbar-content">
      <input id="menu-toggle" type="checkbox" v-model="isMenuOpen" />
      <label class="menu-button-container" for="menu-toggle">
        <div class="menu-button"></div>
      </label>
      <ul :class="['menu', { 'menu-open': isMenuOpen }]">
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
    <p>Copyright&copy; 2024-2025 Weroni-K All Rights Reserved.</p>
  </footer>
</template>

<script setup>
import { onMounted, onUnmounted, watch, ref } from 'vue'
import Home from './components/HomeSection.vue'
import About from './components/AboutSection.vue'
import Projects from './components/ProjectsSection.vue'
import Contact from './components/ContactSection.vue'
import ScrollToTopButton from './components/ScrollToTopButton.vue'
import GitHubIcon from './components/main-manu-components/GitHubIcon.vue'
import LinkedInIcon from './components/main-manu-components/LinkedInIcon.vue'
import AOS from 'aos'

onMounted(() => {
  AOS.refresh()
})
const isDarkMode = ref(false)
const isMenuOpen = ref(false)
const isSticky = ref(false)

const toggleDarkMode = () => {
  isDarkMode.value = !isDarkMode.value
  document.documentElement.classList.toggle('dark-theme', isDarkMode.value)
}

// Loads dark mode preferences from localStorage
if (localStorage.getItem('dark-mode') === 'true') {
  isDarkMode.value = true
  document.documentElement.classList.add('dark-theme')
}

// Saves dark mode preferences to localStorage
watch(isDarkMode, (newValue) => {
  localStorage.setItem('dark-mode', newValue)
})

onMounted(() => {
  const handleScroll = () => {
    isSticky.value = window.scrollY > 120
  }
  window.addEventListener('scroll', handleScroll)

  onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll)
  })
})
</script>

<style scoped>
.toggle-theme {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  margin-right: 16px;
}

.theme-switch {
  position: relative;
  display: inline-block;
  width: 40px;
  height: 24px;
}

.theme-switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: var(--color-bg);
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 34px;
  /* border: 1px solid var(--color-accent); */
}

.slider:before {
  position: absolute;
  content: '';
  height: 20px;
  aspect-ratio: 1;
  left: 2px;
  bottom: 2px;
  background-color: var(--color-neutral-white);
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 50%;
}

.slider:hover::before,
input:checked + .slider:hover::before {
  background-color: var(--color-accent);
}

input:checked + .slider {
  background-color: var(--color-bg);
}

input:focus + .slider {
  box-shadow: 0 0 1px var(--color-bg);
}

input:checked + .slider:before {
  -webkit-transform: translateX(16px);
  -ms-transform: translateX(16px);
  transform: translateX(16px);
  background-color: var(--color-neutral-grey);
}

.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}

.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 100;
  max-width: 100%;
  background-color: var(--color-primary);
  transition:
    background-color 0.3s ease,
    box-shadow 0.3s ease;
}

.navbar.sticky {
  background-color: var(--color-primary);
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  max-width: 1024px;
  border-radius: 50px;
  margin: auto;
  left: 50%;
  transform: translateX(-50%);
}

.navbar-content {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: flex-end;
  height: 64px;
  padding: 0 1rem;
  max-width: 1600px;
  width: 100%;
}

.menu {
  display: flex;
  flex-direction: row;
  list-style-type: none;
  align-items: center;
  justify-content: flex-end;
  margin: 0;
  padding: 0;
}

.menu li {
  font-weight: bold;
  font-size: 20px;
  margin: 0 24px 0 0;
  a {
    text-decoration: none;
    cursor: pointer;
    color: var(--color-text);
  }
  a:hover {
    color: var(--color-accent);
    text-decoration: underline;
  }
}

.menu li:nth-last-child(2) {
  margin: 0 8px 0 0;
}
.menu li:last-child {
  margin: 0 24px 0 0;
}

.menu a {
  color: var(--color-text);
}

.menu a svg {
  vertical-align: middle;
}

.menu .menu-icon path {
  stroke: currentColor;
}

.menu-button-container {
  margin: 0 16px 0 0;
  display: none;
  height: 100%;
  width: 30px;
  cursor: pointer;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

#menu-toggle {
  display: none;
}

.menu-button:hover,
.menu-button:hover::before,
.menu-button:hover::after {
  background-color: var(--color-accent);
}

.menu-button,
.menu-button::before,
.menu-button::after {
  display: block;
  position: absolute;
  height: 4px;
  width: 30px;
  transition: transform 400ms cubic-bezier(0.23, 1, 0.32, 1);
  border-radius: 2px;
}

.menu-button,
.menu-button::before,
.menu-button::after {
  background-color: var(--color-text);
}

.menu-button::before {
  content: '';
  margin-top: -8px;
}

.menu-button::after {
  content: '';
  margin-top: 8px;
}

#menu-toggle:checked + .menu-button-container .menu-button::before {
  margin-top: 0px;
  transform: rotate(405deg);
}

#menu-toggle:checked + .menu-button-container .menu-button {
  background: var(--color-primary);
}

#menu-toggle:checked + .menu-button-container .menu-button::after {
  margin-top: 0px;
  transform: rotate(-405deg);
}

section {
  width: 100%;
  max-width: 1200px;
  margin: auto;
}

footer {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0;
  padding: 4px;
  height: auto;
  max-height: 3rem;
  p {
    font-size: 16px;
    text-align: center;
  }
}

.navbar.menu-open {
  border-radius: 30px 30px 0 0;
}

.menu {
  border-bottom: none;
  transition: border-bottom 0.3s ease;
}

.menu.menu-open {
  border-radius: 0 0 20px 20px;
}

.menu.menu-open li {
  margin-inline: 0;
}

.menu.menu-open li:not(:last-child) {
  border-bottom: 0.1px solid rgba(255, 255, 255, 0.699);
}

.menu.menu-open li:last-child {
  margin-bottom: 4px;
}

@media (min-width: 1600px) {
  .navbar {
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    max-width: 1600px;
    border-radius: 50px;
    margin: auto;
    left: 50%;
    transform: translateX(-50%);
  }
  .navbar-content {
    padding: 0 16px;
  }
}

@media (max-width: 1248px) {
  .navbar {
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    max-width: 1024px;
    border-radius: 50px;
    margin: auto;
    left: 50%;
    transform: translateX(-50%);
  }
  .navbar-content {
    padding: 0 16px;
    height: 56px;
  }
  .menu {
    top: 56px;
  }
  footer p {
    font-size: 14px !important;
  }
}

@media (max-width: 768px) {
  .navbar-content {
    height: 48px;
  }
  .menu-button-container {
    display: flex;
  }
  .menu {
    position: absolute;
    top: 48px;
    left: 0;
    width: 100%;
    flex-direction: column;
    background-color: var(--color-primary);
    display: none;
    transition: all 0.3s ease-in-out;
  }
  .menu li {
    width: 100%;
    text-align: center;
    padding: 12px 0;
  }
  .menu li a {
    width: 100%;
    display: block;
  }
  #menu-toggle:checked ~ .menu {
    display: flex;
  }
  footer p {
    font-size: 12px !important;
  }
}
</style>
