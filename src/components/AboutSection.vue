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
  gap: 2rem;
  justify-content: center;
  align-items: flex-start;
  padding: 2rem 4rem;
  color: var(--color-neutral-grey);
  background-color: var(--color-secondary);
  position: relative;
  width: 90%;
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

.right {
  align-self: center;
}

.my-avatar {
  min-width: 200px;
  width: auto;
  max-width: 25rem;
  aspect-ratio: 1;
  border-radius: 360px;
  border: 2px solid var(--color-text);
  object-fit: cover;
  display: inline-block;
}

.my-avatar:hover {
  border: 2px solid var(--color-accent);
}

.dark-theme .my-avatar {
  filter: brightness(85%);
}

.about-btn {
  display: flex;
  flex-direction: row;
  justify-content: left;
  margin: 4rem auto 0;
  z-index: 10;
}

.about-btn button {
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

.about-btn button:hover {
  transform: scale(1.01) rotate(-359.2deg);
  opacity: 1;
  cursor: pointer;
  border-color: var(--color-accent);
  color: var(--color-accent);
  background-color: var(--color-text);
}

.left {
  display: flex;
  flex-direction: column;
  max-width: 60%;
  padding: 0;
  margin: 0;
  justify-content: center;
  align-items: flex-start;
  color: var(--color-text);
}

.right {
  max-width: 40%;
}

@media (max-width: 1248px) {
  #about {
    width: 100%;
    margin: 14rem 0 auto;
    gap: 1rem;
    padding: 2rem 2rem;
  }
  .my-avatar {
    min-width: 200px;
    width: auto;
    max-width: 20rem;
  }
  .about-btn button {
    font-size: 22px;
  }
}

@media screen and (max-width: 768px) {
  #about {
    flex-wrap: wrap-reverse;
    text-align: center;
    margin: 6rem 0 0;
    padding: 4rem 1rem 3rem;
  }
  .left {
    margin-inline: calc(24px - 1rem);
    align-items: center;
    max-width: 100%;
  }
  .right {
    max-width: 100%;
    margin-inline: calc(24px - 1rem);
  }
  .about-btn {
    margin-top: 2rem;
    button {
      font-size: 20px;
    }
  }
  .my-avatar {
    min-width: 200px;
    width: auto;
    max-width: 15rem;
  }
}
</style>
