<template>
  <v-app :theme="theme">
    <v-app-bar id="topnav" density="compact">
      <v-app-bar-title><a class="logobrand" href="/">
          <v-icon start><v-img src="/images/logo.png"></v-img></v-icon>Elite Kids
        </a></v-app-bar-title>

      <v-list-item title="Home" value="home" href="/"></v-list-item>
      <v-list-item title="Characters" value="Characters" prepend-icon="fas fa-mask" href="/characters"></v-list-item>
      <v-list-item title="Monsters" value="Monsters" prepend-icon="fas fa-spaghetti-monster-flying" href="/monsters"></v-list-item>
      <v-list-item title="Places" value="Places" prepend-icon="fas fa-globe" href="/places"></v-list-item>
      <v-list-item title="Videos" value="Videos" prepend-icon="fas fa-video" href="/videos"></v-list-item>
      <v-list-item title="Stories" value="Stories" prepend-icon="fas fa-book" href="/stories"></v-list-item>
      <v-spacer></v-spacer>

      <div class="d-flex align-center flex-column flex-sm-row fill-height">
        <v-col>
          <v-btn :prepend-icon="theme === 'dark' ? 'fas fa-sun' : 'fas fa-moon'" @click="onClick"></v-btn>
        </v-col>
      </div>
    </v-app-bar>

    <v-main>
      <v-card>
        <v-layout>
          <v-main id="sidebarNav"></v-main>
          <main id="mainSection">
            <slot />
          </main>
        </v-layout>
      </v-card>
      <FooterNav />
    </v-main>
  </v-app>
</template>

<script>
import search from '../components/Search/search.vue'

  export default {
    data() {
      return {
        components: { search },
        drawer: null,
        location: 'bottom',
        rail: true,
        loaded: false,
        loading: false,
      }
    },

    methods: {
      onClick() {
        this.loading = true

        setTimeout(() => {
          this.loading = false
          this.loaded = true
        }, 2000)
      },
    },
  }
</script>

<script setup>
  import {
    ref
  } from 'vue'

  const theme = ref('light')

  function onClick() {
    theme.value = theme.value === 'light' ? 'dark' : 'light'
  };

</script>