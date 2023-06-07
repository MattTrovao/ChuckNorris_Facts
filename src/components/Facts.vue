<template>
  <main class="box">
    <template v-if="fact">
      <div class="pictures">
        <img
          :src="factImg.url"
          alt="Chuck Norris Picture, in a way is like he is saying the facts about himself"
          draggable="false"
        />
      </div>
      <div class="facts">
        <h2>
          {{ fact }}
        </h2>
      </div>
    </template>
  </main>

  <div class="actions">
    <button class="actions__btn new" @click="getFact()">New fact</button>

    <button class="actions__btn share" @click="shareFact()">
      Share on whatsapp
    </button>

    <button
      class="actions__btn copy"
      @click="copyFact()"
      :disabled="copyDisabled"
    >
      Copy text
    </button>
  </div>
</template>

<script>
import { onMounted, ref } from "vue";
import api from "../axios/api";

import Fact1 from "../assets/pictures/Fact1.png";
import Fact2 from "../assets/pictures/Fact2.png";
import Fact3 from "../assets/pictures/Fact3.png";
import Fact4 from "../assets/pictures/Fact4.png";
import Fact5 from "../assets/pictures/Fact5.png";

export default {
  setup() {
    const factImg = ref({});

    const factsImages = ref([
      {
        id: 1,
        url: Fact1,
      },
      {
        id: 2,
        url: Fact2,
      },
      {
        id: 3,
        url: Fact3,
      },
      {
        id: 4,
        url: Fact4,
      },
      {
        id: 5,
        url: Fact5,
      },
    ]);

    function getFactImage(images) {
      return images[Math.floor(Math.random() * images.length)];
    }

    const fact = ref(null);

    async function getFact() {
      let response = await api();

      if (response.data.value) {
        fact.value = response.data.value;

        factImg.value = getFactImage(factsImages.value);
      }
    }

    function shareFact() {
      window.open(`
    https://api.whatsapp.com/send?text=Here is a true fact about Chuck Norris: ${fact.value}
    `);
    }

    const copyDisabled = ref(false);
    function copyFact() {
      copyDisabled.value = true;
      setTimeout(() => {
        navigator.clipboard.writeText(
          `Here is a true fact about Chuck Norris: ${fact.value}`
        );
        copyDisabled.value = false;
      }, 1500);
    }

    onMounted(() => {
      getFact();
    });

    return {
      factImg,
      fact,
      getFact,
      shareFact,
      copyFact,
      copyDisabled,
    };
  },
};
</script>

<style>
</style>