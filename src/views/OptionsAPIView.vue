<template>
  <main>
    <h2>Options API</h2>
  </main>
</template>


<script>
export default {
  name: "OptionAPI",
  data() {
    return { name: "ali" };
  },
  methods: {
    getName() {
      return this.name;
    },
  },
};
</script>
<style scoped>
main {
  height: 100vh;
  display: flex;
  justify-content: center;
}
</style>