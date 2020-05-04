<template>
  <div class="container">
    <h1 class="title">Multiplication Helper</h1>
    <div class="border-solid w-full h-auto">
      <NumberGenerator />
    </div>
  </div>
</template>

<script>
import NumberGenerator from "~/components/NumberGenerator.vue";

export default {
  components: {
    NumberGenerator
  }
};
</script>

<style lang="scss">
/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/

body {
  background-color: rgba(lightcoral, 0.3);
}

.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: center;
  text-align: center;
  overflow: hidden;
  padding: 0 1rem;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 2rem;
  color: #35495e;
  letter-spacing: 1px;
  margin-bottom: 2rem;

  @media (min-width: 768px) {
    font-size: 5rem;
  }
}

.links {
  padding-top: 15px;
}
</style>
