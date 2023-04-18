<template>
  <v-container>
    <h1 class="text--secondary mb-3 mt-3">My ads</h1>
    <v-card v-for="ad in myAds" :key="ad.id" class="mx-auto" max-width="1000">
      <v-row>
        <v-img height="400px" :src="ad.src" cover></v-img>
        <v-spacer></v-spacer>
      </v-row>

      <v-row>
        <v-card-text>
          <h2 class="text--primary">{{ ad.title }}</h2>
          <p>{{ ad.desc }}</p>
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>

          <v-btn color="primary" variant="text" :to="'/ad/' + ad.id">
            Open
          </v-btn>

          <v-spacer></v-spacer>
        </v-card-actions>
      </v-row>
    </v-card>
  </v-container>
</template>

<script>
export default {
  props: ["id"],
  computed: {
    ad() {
      const id = this.id;
      return this.$store.getters.adById(id);
    },
  },
};
</script>
