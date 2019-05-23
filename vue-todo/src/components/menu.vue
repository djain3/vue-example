<template>
  <div class="page-container">
    <md-app md-mode="reveal">
      <md-app-toolbar class="md-primary">
        <span class="md-title">To Do Project</span>
      </md-app-toolbar>
      <md-app-content>
      </md-app-content>
    </md-app>
  </div>
</template>

<style lang="scss" scoped>
  .md-app {
    height: 100vh;
    border: 1px solid rgba(#000, .12);
  }
</style>

<script>
import Cards from './cards.vue'
export default {
  name: 'Reveal',
  components: {
      Cards
  }
}
</script>
