<template>
  <div :class="`warning ${position}`">
    <img src="../assets/icon.svg" alt="WARNING" class="warning__icon">

    <p class="warning__text">
      Everything here is 100% true!!! <br/><br/>
      If you don't believe, Chuck Noris will visit you!!!
    </p>
  </div>
</template>

<script>
import {ref} from 'vue'
export default {
  props: {
    position: {
      type: String,
      required: true,
    }
  },
  setup(props){
    const position = ref(props.position)

    return{
      position,
    }
  }
}
</script>

<style>

</style>