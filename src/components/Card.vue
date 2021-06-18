<template>
  <v-card
    class="my-12"
  >
    <v-img
      height="200px"
      :src="backgroundImage"
    ></v-img>
    <v-row>
      <v-col cols="4">
        <v-container>
          <v-avatar size="100">
            <img
              alt="user"
              :src="character.image"
              contain
            >
          </v-avatar>
        </v-container>
      </v-col>
      <v-col cols="8">
        <v-card-title>{{ character.name }}</v-card-title>
        <v-card-text>
          <div class="text-subtitle-1">
            {{ character.house }}
          </div>
        </v-card-text>
      </v-col>
    </v-row>
    <v-card-text>
      <v-row
        align="center"
        class="mx-0"
      >
      </v-row>
      <div>
        {{ character.name }} was born in {{ character.yearOfBirth }}. {{ getPronoun() }} wand is
        made of {{ character.wand.wood }}, with a core of a {{ character.wand.core }} and a length
        of {{ character.wand.length }} inches. {{ getPronoun() }} patronus is a
        {{ character.patronus }}
      </div>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  name: 'Card',
  props: {
    character: Object,
    backgroundImage: String,
  },
  beforeMount() {
    console.log('BackgroundImage: ', this.backgroundImage);
  },
  methods: {
    getPronoun() {
      return this.character.gender === 'male' ? 'His' : 'Her';
    },
  },
};
</script>

<style scoped>

</style>
