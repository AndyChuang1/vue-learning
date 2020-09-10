<template>
  <div class="infoCard">
    <Header msg="I'm infoCard Page"></Header>
    <div class="cardGroup">
      <Card
        v-for="(data, idx) in cardInfo"
        :userId="data.userId"
        :id="data.id"
        :title="data.title"
        :completed="data.complete"
        :key="idx"
      ></Card>
    </div>
  </div>
</template>
<script>
import Header from '@/components/Header.vue';
import Card from '@/components/Card.vue';

export default {
  components: {
    Header,
    Card,
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
};
</script>
<style lang="scss" scoped>
.cardGroup {
  display: flex;
}
</style>
