<template>
  <v-container>
    <v-layout>
      <v-flex>
        <v-btn block
               color="accent"
               nuxt
               to="/about">
          Go to About Page
        </v-btn>
      </v-flex>
    </v-layout>
    <v-layout>
      <v-flex>
        <v-card>
          <the-user-list :users="users" />
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script lang="ts">
import { NuxtContext } from 'nuxt';
import { Component, Vue } from 'nuxtjs-extensions';

import TheUserList from '../components/TheUserList.vue';

@Component({
  components: {
    TheUserList
  }
})
export default class extends Vue {
  async asyncData({ app }: NuxtContext) {
    const { results } = await app.$axios.$get('/api/users');
    return { users: results };
  }
}
</script>
