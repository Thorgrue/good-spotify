<template>
  <div class="home">
    <h1 :class="underline ? 'underline' : ''" @click="activeUnderline">text</h1>
    <HelloWorld :msg="msg"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';

export default {
  name: 'Home',
  components: {
    HelloWorld,
  },
  data() {
    return {
      msg: 'je suis là',
      underline: false,
    };
  },
  methods: {
    activeUnderline() {
      this.underline = !this.underline;
    },
  },
};
</script>
