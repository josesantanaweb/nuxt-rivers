<template>
  <nav class="navbar">
    <div class="logo">
      <svg
        class="fill-current h-8 w-8 mr-2"
        width="54"
        height="54"
        viewBox="0 0 54 54"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M13.5 22.1c1.8-7.2 6.3-10.8 13.5-10.8 10.8 0 12.15 8.1 17.55 9.45 3.6.9 6.75-.45 9.45-4.05-1.8 7.2-6.3 10.8-13.5 10.8-10.8 0-12.15-8.1-17.55-9.45-3.6-.9-6.75.45-9.45 4.05zM0 38.3c1.8-7.2 6.3-10.8 13.5-10.8 10.8 0 12.15 8.1 17.55 9.45 3.6.9 6.75-.45 9.45-4.05-1.8 7.2-6.3 10.8-13.5 10.8-10.8 0-12.15-8.1-17.55-9.45-3.6-.9-6.75.45-9.45 4.05z"
        />
      </svg>
      <span class="font-semibold text-xl tracking-tight">Nuxt Rivers</span>
    </div>
    <div class="toggle">
      <span
      v-for="theme of themes"
        :key="theme"
        @click="setTheme(theme.theme)"
      >
        <font-awesome-icon :icon="['fas', theme.icon]"/>
      </span>
    </div>
  </nav>
</template>
<script>
import Navbar from "../components/Navbar";
import Rivers from "../components/Rivers";
export default {
  name: "index",
  components: { Navbar, Rivers },
  data() {
    return {
      themes: [
        {
          theme: 'light',
          icon: 'lightbulb'
        },
        {
          theme: 'dark',
          icon: 'moon'
        }
      ],
    };
  },
  methods: {
    setTheme(color) {
      $nuxt.$colorMode.preference = color;
      const html = document.getElementsByTagName("html")[0];
      if (color === "dark") {
        html.classList.add("dark");
      } else {
        html.classList.remove("dark");
      }
    },
  },
  mounted() {
    const html = document.getElementsByTagName("html")[0];
    if (html.classList.contains("dark-mode")) {
      html.classList.add("dark");
    }
  },
};
</script>

