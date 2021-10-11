<template>
  <div id="TextEdit" class="text-center">
    <h3 class="card mx-auto my-2">
      {{ title }}
    </h3>
    <p class="my-1">{{ paragraph }}</p>
    <ol class="mx-auto" style="width: 200px">
      <li>
        <a href="#">{{ user.name }}</a>
      </li>
      <li>
        <a href="#">{{ user.age }}</a>
      </li>
      <li>
        <a href="#">{{ user.address }}</a>
      </li>
    </ol>
  </div>
</template>

<script>
  export default {
    name: 'TextEdit',
    props: {
      title: {
        type: String,
        default: 'Hello',
        validator(value) {
          return ['success', 'warning', 'danger'].indexOf(value) !== -1;
        },
        required: false,
      },
      paragraph: {
        type: String,
        required: true,
      },
      user: Object,
    },
  };
</script>

<style lang="scss" scoped>
  .card {
    border: 1px solid #000;
    padding: 10px;
    border-radius: 5px;
    width: 200px;
  }
</style>
