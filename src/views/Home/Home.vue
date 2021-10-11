<template>
  <div class="home">
    <div>
      <!-- [v-bind:] <=> [:] -->
      <h1 v-bind:title="timeMsg">{{ title }}</h1>
      <p>{{ msg }}</p>
    </div>

    <!-- Alt + W -->
    <div>
      <h3 v-if="seen">You can see me!</h3>
      <h3 v-else class="hide">I am hiding!</h3>
      <!-- [v-on:] <=> [@] -->
      <button v-on:click="seen = !seen">Show/Hide</button>
    </div>

    <!-- List Rendering -->
    <ol>
      <li v-for="todo in todos" :key="todo.id">
        {{ todo.text }}
      </li>
    </ol>

    <!-- Random -->
    <RandomNumber />

    <!-- TextEdit -->
    <TextEdit :title="title" :paragraph="msg" :user="user" />

    <div>
      <button class="btn btn-success btn-sm mx-auto d-block" style="width: 120px" @click="log()">
        Show Data
      </button>
    </div>

    <div>
      <p>Thông điệp ban đầu: "{{ message }}"</p>
      <p>Thông điệp bị đảo ngược bằng tính toán (computed): "{{ reversedMessage }}"</p>
    </div>

    <!-- Binding Class and Style -->
    <div class="d-flex mx-auto justify-content-around" style="width: 500px">
      <div :class="activeClass" class="box">1</div>
      <div :class="activeClass" class="box">2</div>
      <div :class="activeClass" class="box">3</div>
    </div>
    <h3>{{ price | USD }}</h3>

    <div class="mx-auto d-flex justify-content-around align-items-center" style="width: 500px">
      <div class="box" :style="{ zoom: zoom }">BOX</div>
      <Zoom @zoomParent="zoomParent" />
    </div>
  </div>
</template>

<script>
  // @ is an alias to /src
  import RandomNumber from './Child/RandomNumber';
  import TextEdit from './Child/TextEdit';
  import Zoom from './Child/Zoom';

  export default {
    name: 'Home',
    components: {
      RandomNumber,
      TextEdit,
      Zoom,
    },
    data() {
      return {
        zoom: 1,
        price: 80000,
        isActive: true,
        title: 'Hello World !',
        message: 'Happy new year!',
        msg: 'Lorem ipsum dolor sit amet consectetur adipisicing elit.',
        user: {
          name: 'Nam',
          age: 19,
          address: 'Ha Noi',
        },
        timeMsg: 'Time: ' + new Date().toLocaleString(),
        seen: true,
        todos: [
          { id: 1, text: 'Learn JavaScript' },
          { id: 2, text: 'Learn Vue' },
          { id: 3, text: 'Build something awesome' },
          { id: 4, text: 'Learn NodeJS' },
        ],
      };
    },
    filters: {
      USD(val) {
        return (val / 23000).toFixed(2) + ' USD';
      },
    },
    watch: {},
    computed: {
      activeClass() {
        return {
          active: this.isActive,
        };
      },
      reversedMessage() {
        console.log('Computed');
        return this.message.split(' ').reverse().join(' ');
      },
    },
    methods: {
      log() {
        console.log(this._data);
      },
      zoomParent(increase) {
        this.zoom += increase/100;
      },
    },
  };
</script>

<style lang="scss" scoped>
  @import './Home.scss';
</style>
