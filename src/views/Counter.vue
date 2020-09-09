<template>
  <div class="counter">
    <Header msg="I'm counter Page"></Header>
    <h2 class="text">Number:{{ count }}</h2>
    <h2 class="text">Roman Number:{{ romanToInt }}</h2>
    <div class="btn-group">
      <button v-on:click="increase()">+</button>
      <button @click="decrease()">-</button>
    </div>
  </div>
</template>
<script>
import Header from '@/components/Header.vue';

export default {
  components: {
    Header,
  },
  data() {
    return {
      count: 0,
    };
  },
  watch: {
    count(newNumber) {
      if (newNumber === 10 || newNumber === 0) {
        alert(`Number achieve ${newNumber}`);
      }
    },
  },
  computed: {
    romanToInt() {
      const romanMap = {
        1: 'I',
        2: 'II',
        3: 'III',
        4: 'IV',
        5: 'V',
        6: 'VI',
        7: 'VII',
        8: 'VIII',
        9: 'IX',
        10: 'X',
      };

      return romanMap[this.count] || this.count;
    },
  },
  methods: {
    increase() {
      this.count += 1;
    },
    decrease() {
      this.count -= 1;
    },
  },
};
</script>
<style lang="scss" scoped>
.btn-group {
  button {
    width: 30px;
    font-size: 20px;
    &:nth-child(even) {
      margin-left: 0.5rem;
    }
  }
}
</style>
