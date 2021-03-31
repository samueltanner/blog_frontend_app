<template>
  <div class="test">
    <h1>Welcome to the Test Page</h1>
    <h3>{{ message }}</h3>
  </div>
</template>

<style></style>

<script>
export default {
  data: function () {
    return {
      message: "This is a test!",
    };
  },
  created: function () {},
  methods: {},
};
</script>
