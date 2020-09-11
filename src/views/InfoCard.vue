<template>
  <div class="infoCard">
    <Header msg="I'm infoCard Page"></Header>
    <div class="cardGroup">
      <Card
        v-for="(data, idx) in cardInfo"
        :userId="data.userId"
        :id="data.id"
        :title="data.title"
        :completed="data.completed"
        :key="idx"
      ></Card>
    </div>
  </div>
</template>
<script>
import Header from '@/components/Header.vue';
import Card from '@/components/Card.vue';
import axios from 'axios';

export default {
  components: {
    Header,
    Card,
  },
  created() {
    this.getTodoInfo();
  },
  data() {
    return {
      cardInfo: [
        {
          userId: 1,
          id: 1,
          title: 'delectus aut autem',
          completed: false,
        },
        {
          userId: 1,
          id: 2,
          title: 'quis ut nam facilis et officia qui',
          completed: false,
        },
        {
          userId: 1,
          id: 3,
          title: 'fugiat veniam minus',
          completed: true,
        },
      ],
    };
  },
  methods: {
    getTodoInfo() {
      axios
        .get('https://jsonplaceholder.typicode.com/users/1/todos/')
        .then((data) => {
          this.cardInfo = data.data;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>
<style lang="scss" scoped>
.cardGroup {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
