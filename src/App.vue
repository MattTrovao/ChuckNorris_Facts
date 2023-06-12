<template>
  <SealOfTrue position="right" />

  <div class="container">
    <header class="header">
      <h1 class="header__title">
        Chuck Norris Super Real True Facts
      </h1>
    </header>
    
    <Facts />

    <footer class="footer">
      <p class="footer__text">
        Project created using the Chuck Norris API. This website and its creators are not affiliated with Chuck Norris, any motion picture corporation, any television corporation, parent, or affiliate corporation. All motion pictures, products, and brands mentioned on this website are the respective trademarks and copyrights of their owners. <br/>
        Project created by <a href="https://github.com/MattTrovao" target="_blank" rel="noopener noreferrer">MattTrovao</a>
      </p>
    </footer>
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
