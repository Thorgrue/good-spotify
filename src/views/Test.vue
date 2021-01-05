<template>
  <div class="test">
    <h1>This is a test page</h1>
    <fetch-genre-base :accessToken="accessToken" v-if="isLoad"></fetch-genre-base>
  </div>
</template>

<script>
import FetchGenreBase from '../components/FetchGenreBase.vue';

export default {
  components: {
    FetchGenreBase,
  },
  data() {
    return {
      clientId: 'dc244f4173ab48bbbff42e71d617c618',
      clientSecret: '4e40c9fc06f1484caee2405a42d62ea9',
      accessToken: '',
      isLoad: false,
    };
  },
  methods: {
    fetchAccessToken() {
      fetch('https://accounts.spotify.com/api/token', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/x-www-form-urlencoded',
          Authorization: `Basic ${btoa(`${this.clientId}:${this.clientSecret}`)}`,
        },
        body: 'grant_type=client_credentials',
      }).then((response) => response.json())
        .then((data) => {
          this.accessToken = data.access_token;
          this.isLoad = true;
        });
    },
  },
  mounted() {
    this.fetchAccessToken();
  },
};
</script>
