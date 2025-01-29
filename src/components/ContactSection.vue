<template>
  <div id="contact">
    <h1>Contact</h1>
    <h2>I’d love to hear from you! Contact me through any of these options:</h2>
    <ul class="contact-list">
      <li>
        <PhoneIcon />
        <p>+358 40817 4321</p>
      </li>
      <li>
        <MailIcon />
        <p>weronika.kirchner@gmail.com</p>
      </li>
      <li>
        <LinkedInIcon />
        <a href="https://www.linkedin.com/in/weronika-kirchner/" target="blank2"
          ><p>LinkedIn</p>
        </a>
      </li>
      <li>
        <GitHubIcon />
        <a href="https://github.com/Weroni-K" target="blank2"><p>GitHub</p> </a>
      </li>
    </ul>
  </div>
</template>

<script setup>
import PhoneIcon from './contact-components/PhoneIcon.vue'
import MailIcon from './contact-components/MailIcon.vue'
import LinkedInIcon from './contact-components/LinkedInIcon.vue'
import GitHubIcon from './contact-components/GitHubIcon.vue'
</script>

<style scoped>
#contact {
  margin-top: 0;
  padding-top: 20px;
  padding-bottom: 144px;
  padding-left: 160px;
}

.contact-list {
  display: flex;
  flex-direction: column;
  list-style-type: none;
  margin: 2rem 0 0 0;
  padding: 0;
}

.contact-list li {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 12px;
}

p {
  font-size: 24px;
}

a {
  color: var(--color-text);
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
  color: var(--color-accent);
}

p:hover {
  color: var(--color-accent);
}

li:hover {
  .icon {
    stroke: var(--color-accent);
  }
}
</style>
