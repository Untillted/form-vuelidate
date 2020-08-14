<template>
  <div id="app">
    <div class="wrapper">
      <section class="form">
        <Form />
      </section>
    </div>
  </div>
</template>

<script>
import Form from "@/components/Form.vue";
export default {
  components: {
    Form,
  },
};
</script>

<style lang="scss">
#app {
  width: 100%;
  height: 100%;
  font-family: "Roboto Slab", serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000;
  overflow: hidden;
  background: rgb(80, 60, 94);
  background: rgb(80, 60, 94);
  background: linear-gradient(
    90deg,
    rgba(80, 60, 94, 1) 0%,
    rgba(74, 73, 156, 1) 0%,
    rgba(75, 112, 203, 1) 79%,
    rgba(78, 103, 176, 1) 100%
  );
}
* {
  padding: 0;
  margin: 0;
}
*:focus {
  outline: none;
}
*,
*:before,
*:after {
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
.container {
  width: 1024px;
  margin: 0 auto;
  @media (max-width: 1023px) {
    max-width: 970px;
  }
  @media (max-width: 991px) {
    max-width: 750px;
  }
  @media (max-width: 759px) {
    max-width: 610px;
  }
  @media (max-width: 549px) {
    max-width: 361px;
  }
}
</style>
