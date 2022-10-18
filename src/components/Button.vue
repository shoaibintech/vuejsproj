<template>
  <button
    @click="onClick()"
    :style="{ background: bgcolor }"
    class="button-common"
  >
    <h5>
      {{ title }}
    </h5>
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    title: String,
    bgcolor: String,
  },
  methods: {
    onClick() {
      console.log("button clicked");
      this.$emit("toggle-add-task");
    },
  },
};
</script>

<style scoped>
.button-common {
  color: white;
  background-color: black;
  border-radius: 3px;
  padding: 0px 20px;
}
h1 {
}
</style>