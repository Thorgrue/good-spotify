<template>
  <div></div>
</template>

<script>
export default {
  props: {
    accessToken: {
      type: String,
      required: true,
    },
  },
  methods: {
    fetchGenre() {
      fetch('https://api.spotify.com/v1/me', {
        method: 'GET',
        headers: { Authorization: `Bearer ${this.accessToken}` },
      }).then((response) => response.json())
        .then((data) => {
          console.log(data);
        });
    },
  },
  mounted() {
    console.log(this.accessToken);
    this.fetchGenre();
  },
};
</script>
