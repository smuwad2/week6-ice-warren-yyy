<!-- src/components/Ex5.vue -->
<script setup>
import { ref, computed } from 'vue'

const name = ref('')
const job = ref('')
const bio = ref('')

// If you put the image in /public/img/head.jfif, you can reference it as '/img/head.jfif'
const imageUrl = ref('/img/head.jfif')

const bgColor = ref('#f5f5f5')
const textColor = ref('#333')
const fontSize = ref(16) // use v-model.number in template to keep this numeric
const bold = ref(false)
const italic = ref(false)
const underline = ref(false)

const previewStyles = computed(() => ({
  backgroundColor: bgColor.value,
  color: textColor.value,
  fontSize: `${fontSize.value}px`,
}))

function applyTheme(theme) {
  // optional: reset style flags when switching themes
  bold.value = false
  italic.value = false
  underline.value = false

  if (theme === 'dark') {
    bgColor.value = '#333'
    textColor.value = '#fff'
  } else if (theme === 'light') {
    bgColor.value = '#fff'
    textColor.value = '#000'
  } else if (theme === 'neon') {
    bgColor.value = '#39ff14'
    textColor.value = '#000'
    bold.value = true
  }
}
</script>

<template>
  <div class="container">
    <!-- Form Section -->
    <div class="form-section">
      <h2>Customize Profile</h2>

      <label>Name:</label><br />
      <input id="name" v-model="name" placeholder="Your Name" /><br /><br />

      <label>Job Title:</label><br />
      <input id="job" v-model="job" placeholder="Web Developer" /><br /><br />

      <label>Bio:</label><br />
      <textarea id="bio" v-model="bio" rows="3" placeholder="A short bio..."></textarea><br /><br />

      <label>Profile Image URL:</label><br />
      <input id="imageUrl" v-model="imageUrl" placeholder="https://example.com/me.jpg" /><br /><br />

      <label>Background Color:</label>
      <input id="bgColor" type="color" v-model="bgColor" /><br /><br />

      <label>Text Color:</label>
      <input id="textColor" type="color" v-model="textColor" /><br /><br />

      <label>Font Size:</label>
      <input id="fontSize" type="range" min="12" max="32" v-model.number="fontSize" />
      {{ fontSize }}px<br /><br />

      <label>Font Styles:</label><br />
      <input type="checkbox" v-model="bold" /> Bold
      <input type="checkbox" v-model="italic" /> Italic
      <input type="checkbox" v-model="underline" /> Underline<br /><br />

      <label>Theme Presets:</label><br />
      <button class="theme-button" @click="applyTheme('dark')">Dark</button>
      <button class="theme-button" @click="applyTheme('light')">Light</button>
      <button class="theme-button" @click="applyTheme('neon')">Neon</button><br /><br />
    </div>

    <!-- Preview Section -->
    <div class="preview-section">
      <h2>Live Preview</h2>
      <div
        class="preview-card"
        :style="previewStyles"
        :class="{ bold, italic, underline }"
      >
        <img :src="imageUrl" alt="Profile image" class="preview-img" />
        <h3>{{ name || 'Your Name' }}</h3>
        <h4>{{ job || 'Job Title' }}</h4>
        <p>{{ bio || 'Write something about yourself...' }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  gap: 20px;
  padding: 20px;
  font-family: sans-serif;
}
.form-section,
.preview-section {
  width: 50%;
}
.preview-card {
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  text-align: center;
  transition: all 0.3s ease;
}
.preview-img {
  width: 100px;
  height: 100px;
  object-fit: cover;
  border-radius: 50%;
  margin-bottom: 10px;
}
.bold { font-weight: bold; }
.italic { font-style: italic; }
.underline { text-decoration: underline; }
.theme-button {
  margin: 5px;
  padding: 5px 10px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>
