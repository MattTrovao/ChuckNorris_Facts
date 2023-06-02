<template>
  <div class="picture"></div>
  <div class="facts">
    <h2>
      {{ fact }}
    </h2>
  </div>

  <div class="actions">
    <button class="actions__btn new" @click="getFact()">
      New fact
    </button>

    <button class="actions__btn share" @click="shareFact()">
      Share on whatsapp
    </button>

    <button class="actions__btn copy" @click="shareFact()">
      Copy text
    </button>
  </div>
</template>

<script>
import { onMounted, ref } from 'vue'

import api from '../axios/api'
export default {
setup(){
  const fact = ref(null)

  async function getFact() {
    let response = await api()

    if(response.data.value){
      fact.value = response.data.value
    };
  }

  function shareFact() {
    window.open(`
    https://api.whatsapp.com/send?text=Here is a true fact about Chuck Noris: ${fact.value}
    `)
  }

  onMounted(() => {
    getFact()
  })

  return{
    fact,
    getFact,
    shareFact,
  }
}
}
</script>

<style>

</style>