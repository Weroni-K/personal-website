<template>
  <div id="about">
    <div class="left">
      <h1>About Me</h1>
      <h2>
        Passionate about web development and design, thriving on exciting challenges. Adaptable,
        collaborative, and a fast learner. Let's create something amazing together!
      </h2>
      <div class="about-btn">
        <a :href="CV" without rel="noopener noreferrer" target="_blank">
          <button type="button" trailingIcon="" label="CV">See my CV</button>
        </a>
      </div>
    </div>
    <div class="right">
      <div><img class="my-avatar" :src="Avatar" alt="avatar" /></div>
    </div>
  </div>
</template>

<script setup>
import Avatar from '../assets/media/profile1.png'
import CV from '../assets/media/CV.pdf'
</script>

<style scoped>
h1 {
  color: var(--color-primary);
}
h2 {
  color: var(--color-text);
}
p {
  color: var(--color-text);
}

#about {
  display: flex;
  flex-direction: row;
  margin: 18rem auto auto;
  flex-wrap: none;
  flex: 1 auto;
  max-width: 80%;
  gap: 96px;
  justify-content: center;
  align-items: flex-start;
  padding-left: 160px;
  padding-right: 208px;
  padding-bottom: 20px;
  padding-top: 20px;
  color: var(--color-neutral-grey);
  background-color: var(--color-secondary);
  position: relative;
}

#about::before,
#about::after {
  content: '';
  position: absolute;
  width: 5%;
  height: 25%;
  border: solid var(--color-text);
}

#about::before {
  top: 0;
  right: 0;
  border-width: 2px 2px 0 0;
}

#about::after {
  bottom: 0;
  left: 0;
  border-width: 0 0 2px 2px;
}

#about .my-avatar {
  width: 400px;
  height: 400px;
  border-radius: 360px;
  border: 2px solid var(--color-text);
}

#about .my-avatar:hover {
  border: 2px solid var(--color-accent);
}

.dark-theme #about .my-avatar {
  filter: brightness(85%);
}

#about .about-btn {
  display: flex;
  flex-direction: row;
  justify-content: left;
  margin-left: 344px;
  margin-top: 64px;
  margin-bottom: 0;
  z-index: 10;
}

#about .about-btn button {
  z-index: 10;
  opacity: 0.84;
  font-weight: 500;
  background-color: var(--color-secondary);
  border: solid;
  outline: none;
  border-color: var(--color-text);
  color: var(--color-text);
  font-size: 24px;
  line-height: 32px;
  padding: 8px;
  border-radius: 4px;
  min-width: 192px;
  min-height: 56px;
}

#about .about-btn button:hover {
  transform: scale(1.01) rotate(-359.2deg);
  opacity: 1;
  cursor: pointer;
  border-color: var(--color-accent);
  color: var(--color-accent);
  background-color: var(--color-text);
}
</style>
