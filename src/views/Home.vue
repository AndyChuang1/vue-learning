<template>
  <div class="home">
    <Header msg="I'm Home page"></Header>
    <img alt="Vue logo" src="../assets/logo.png" />
    <h1>{{ text }}</h1>
  </div>
</template>

<script>
// @ is an alias to /src
import Header from '@/components/Header.vue';

export default {
  name: 'Home',
  components: { Header },
  data() {
    return {
      text: 'Hello world!',
    };
  },
};
</script>
