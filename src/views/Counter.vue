<template>
  <div class="counter">
    <Header msg="I'm counter Page"></Header>
    <h2 class="text" v-bind:style="{ color: activeColor, 'font-size': fontSize }">
      Number:{{ count }}
    </h2>
    <h2 :class="['text', { 'red-bigFont': count === 10, 'green-smFont': count === 0 }]">
      Roman Number:{{ romanToInt }}
    </h2>
    <div class="btn-group">
      <button v-if="count < 10" v-on:click="increase()">+</button>
      <button v-show="count > 0" @click="decrease()">-</button>
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
      activeColor: 'green',
      fontSize: '12px',
    };
  },
  watch: {
    count(newNumber) {
      if (newNumber === 10 || newNumber === 0) {
        alert(`Number achieve ${newNumber}`);
      }
      if (newNumber === 10) {
        this.activeColor = 'red';
        this.fontSize = '30px';
      } else if (newNumber === 0) {
        this.activeColor = 'green';
        this.fontSize = '12px';
      } else {
        this.activeColor = 'black';
        this.fontSize = '24px';
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
.red-bigFont {
  color: red;
  font-size: 30px;
}
.green-smFont {
  color: green;
  font-size: 12px;
}
</style>
