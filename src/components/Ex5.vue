<!DOCTYPE html>
<html>

<head>
  <title>Advanced Profile Card Builder</title>
  <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
  <style>
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

    .bold {
      font-weight: bold;
    }

    .italic {
      font-style: italic;
    }

    .underline {
      text-decoration: underline;
    }

    .theme-button {
      margin: 5px;
      padding: 5px 10px;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }
  </style>
  <!-- Vue 3 -->
  <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>

</head>

<body>

  <div id="app" class="container">
    <!-- Form Section -->
    <div class="form-section">
      <h2>Customize Profile</h2>

      <label>Name:</label><br>
      <input id="name" v-model="name" placeholder="Your Name"><br><br>

      <label>Job Title:</label><br>
      <input id="job" v-model="job" placeholder="Web Developer"><br><br>

      <label>Bio:</label><br>
      <textarea id="bio" v-model="bio" rows="3" placeholder="A short bio..."></textarea><br><br>

      <label>Profile Image URL:</label><br>
      <input id="imageUrl" v-model="imageUrl" placeholder="https://example.com/me.jpg"><br><br>

      <label>Background Color:</label>
      <input id="bgColor" type="color" v-model="bgColor"><br><br>

      <label>Text Color:</label>
      <input id="textColor" type="color" v-model="textColor"><br><br>

      <label>Font Size:</label>
      <input id="fontSize" type="range" min="12" max="32" v-model="fontSize"> {{ fontSize }}px<br><br>

      <label>Font Styles:</label><br>
      <input type="checkbox" v-model="bold"> Bold
      <input type="checkbox" v-model="italic"> Italic
      <input type="checkbox" v-model="underline"> Underline<br><br>

      <label>Theme Presets:</label><br>
      <button class="theme-button" @click="applyTheme('dark')">Dark</button>
      <button class="theme-button" @click="applyTheme('light')">Light</button>
      <button class="theme-button" @click="applyTheme('neon')">Neon</button><br><br>

    </div>

    <!-- Preview Section -->
    <div class="preview-section">
      <h2>Live Preview</h2>
      <div class="preview-card" :style="previewStyles"
        :class="{'bold': bold, 'italic': italic, 'underline': underline}">
        <img :src="imageUrl" class="preview-img">
        <h3>{{ name || 'Your Name' }}</h3>
        <h4>{{ job || 'Job Title' }}</h4>
        <p>{{ bio || 'Write something about yourself...' }}</p>
      </div>
    </div>
  </div>

  <script>
    const app = Vue.createApp({
      data() {
        return {
          name: '',
          job: '',
          bio: '',
          imageUrl: './img/head.jfif',
          bgColor: '#f5f5f5',
          textColor: '#333',
          fontSize: 16,
          bold: false,
          italic: false,
          underline: false
        }
      },
      computed: {
        previewStyles() {
          return {
            backgroundColor: this.bgColor,
            color: this.textColor,
            fontSize: this.fontSize + 'px',
          };
        },
      },
      methods: {
        applyTheme(theme) {
          if (theme === 'dark') {
            this.bgColor = '#333';
            this.textColor = '#fff';
          } else if (theme === 'light') {
            this.bgColor = '#fff';
            this.textColor = '#000';
          } else if (theme === 'neon') {
            this.bgColor = '#39ff14';
            this.textColor = '#000';
            this.bold = true;
          }
        }
      }
    });
    const vm = app.mount('#app');
  </script>

</body>

</html>