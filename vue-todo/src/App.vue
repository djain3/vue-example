<template>
  <div class="full-page">
    <toolbar/>
    <fulllogin/>
  </div>
</template>

<script>
import Toolbar from "./components/toolbar.vue";
import fulllogin from "./components/fulllogin.vue";

export default {
  components: {
    Toolbar,
    fulllogin
  }
};
</script>

<style>
</style>
