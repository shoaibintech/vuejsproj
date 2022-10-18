<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']"
  >
    <h3>
      {{ task.text }}
      <i @click="DeleteTask(task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>

<script>
export default {
  beforeCreate() {
    console.log("life cycle method 1 beforeCreate() 1 is called");
    console.log(
      "beforeCreate is the first lifecycle hook that gets called in Vue JS. beforeCreate is called right after a new Vue instance is initialized. Here, the computed properties, watchers, events, data properties, etc., are not set up."
    );
  },
  name: "Task",
  props: {
    task: Object,
  },
  // methods for component

  methods: {
    DeleteTask(id) {
      console.log("elemnt number : " + id + " deleted");
      this.$emit("delete-task", id);
    },
  },

  //life cycle methods of component

  created() {
    console.log(
      "life cycle method 2 created() is called : created is the next lifecycle hook that gets called after the beforeCreate hook. Here, the computed properties, watchers, events, data properties, etc., are also activated. "
    );
  },

  beforeMount() {
    console.log("life cycle method 3 beforeMount() 1 is called");
    console.log(
      "beforeMount is the next lifecycle hook that gets called after the created hook and right before the Vue instance is mounted on the DOM. The template and the styles are all compiled here, but the DOM cannot be manipulated yet."
    );
  },

  mounted() {
    console.log(
      "life cycle method 4 mounted() is called : mounted is the next lifecycle hook that gets called after the beforeMount hook and right after the Vue instance has been mounted. The app component or any other component becomes functional and is ready to use."
    );
  },

  beforeUpdate() {
    console.log(
      " life cycle method 5 beforeupdate()  beforeUpdate is the next lifecycle hook called after the mounted hook. beforeUpdate is called any time a change is made to the data that requires the DOM to be updated."
    );
  },

  updated() {
    console.log(
      "life cycle method 6 updated() updated is the next lifecycle hook. updated is called after the beforeUpdate hook and just after a DOM update has occurred."
    );
  },

  beforeDestroy() {
    console.log(
      "life cycle method 7 beforedestroy() The beforeDestroy hook is called just before a Vue instance is destroyed. The instance and all the methods are still functional. We can do resource management here."
    );
    //    this.msg = null
    //   delete this.msg;
  },

  destroyed() {
    // this.＄destroy()
    console.log(
      "life cycle method 8 destroy() destroyed is the last stage lifecycle hook, where the entire Vue instance gets destroyed. Event listeners, mixins, and all directives get unbounded here."
    );
  },
};
</script>

<style scoped>
.task {
  background-color: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.reminder {
  border-left: 5px solid green;
}

.fas {
  color: red;
}
</style>