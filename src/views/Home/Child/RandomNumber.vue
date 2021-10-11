<template>
  <div id="randomNumber" class="random">
    <h3>{{ numberRandom }}</h3>
    <button class="btn btn-primary btn-sm" @click="randomNumber()">Random number</button>
  </div>
</template>

<script>
  export default {
    name: 'RandomNumber',
    data() {
      return {
        numberRandom: 1,
      };
    },
    methods: {
      randomNumber() {
        let max = 6,
          min = 1;
        let randNum = Math.floor(Math.random() * (max - min + 1) + min);
        this.numberRandom = randNum;
      },
    },
  };
</script>

<style lang="scss" scoped>
.random{
  width: 500px;
  margin: 0 auto;
  text-align: center;
}
</style>
