<template>
  <div>
    <v-row wrap>
      <v-col
        cols="4"
        :key="index"
        v-for="(character, index) in characters"
      >
        <card
          class="item"
          :character="character"
          :background-image="images[character.house]"
        >
        </card>
      </v-col>
    </v-row>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import Card from '@/components/Card.vue';
import gryffindorImage from '@/assets/gryffindor.jpg';
import hufflepuffImage from '@/assets/hufflepuff.jpg';
import ravenclawImage from '@/assets/ravenclaw.jpg';
import slytherinImage from '@/assets/slytherin.jpg';

export default Vue.extend({
  name: 'Home',
  components: { Card },
  beforeMount() {
    fetch('http://hp-api.herokuapp.com/api/characters').then(
      async (response) => {
        this.characters = await response.json();
      },
    );
  },
  data() {
    return {
      characters: [],
      images: {
        Gryffindor: gryffindorImage,
        Ravenclaw: ravenclawImage,
        Hufflepuff: hufflepuffImage,
        Slytherin: slytherinImage,
      },
    };
  },
});
</script>
