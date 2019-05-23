<template>
  <div class="wrapper wrapper-full-page">
    <div class="page-header">
      <div class="container md-offset">
        <div class="md-layout text-center">
          <login/>
        </div>
      </div>
      <div class="footer"></div>
    </div>
  </div>
</template>

<script>
import Login from "./register.vue";
export default {
  components: {
    Login
  }
};
</script>


<style lang="scss">
.wrapper.wrapper-full-page {
  height: auto;
  min-height: 100vh;
}

.page-header {
  height: 100%;
  min-height: 100vh;
  background-position: top;
  background-size: cover;
  margin: 0;
  padding: 0;
  border: 0;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
}

.container {
  display: flex;
  align-items: center;
  width: 100%;
  max-width: 720px;
}
.md-offset {
  margin: auto;
}
.text-center {
    justify-content: center
}
.md-layout {
    width: 100%;
}
</style>

