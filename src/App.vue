<template>
  <SealOfTrue position="right" />

  <div class="container">
    <header class="header">
      <h1 class="header__title">
        Chuck Noris Super Real True Facts
      </h1>
    </header>
    <Facts />
  </div>

  <SealOfTrue position="left" />

</template>

<script>
import Facts from './components/Facts.vue'
import SealOfTrue from './components/SealOfTrue.vue'


export default {
  components: {
    SealOfTrue,
    Facts,
  },
  setup(){}
}

</script>

<style scoped>
</style>
