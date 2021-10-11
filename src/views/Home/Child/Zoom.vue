<template>
  <div id="zoom">
    <button class="btn btn-secondary btn-lg d-block" @click="zoom">Phóng to</button>
  </div>
</template>

<script>
  export default {
    name: 'Zoom',
    methods: {
      zoom() {
        this.$emit('zoomParent', 50);
      },
    },
  };
</script>

<style></style>
