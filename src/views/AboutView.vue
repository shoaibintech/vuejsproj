<template>
  <main>
    <div class="about">
      <div>
        <h1>Watchers in vue js</h1>
        <h2>example 1</h2>
        <p>kilometer to meter conversion and viceversa</p>

        <div id="watchersWrapper">
          Kilometers : <input type="text" v-model="kilometers" /> Meters :
          <input type="text" v-model="meters" />
        </div>

        <h2>example 2</h2>
        <p>double the number</p>

        input a number<input type="text" v-model="input" @change="multiply" />

        number {{ input }} x 2 = {{ result }}
      </div>
      <div>
        <h1>bindings in vue js</h1>

        <div>
          <h2 v-bind:class="{ active: isActive, error: hasError }">
            click button to turn background-color to yellow
          </h2>

          <button @click="changeBG">Change Background Color</button>
        </div>
      </div>

      <div>
        <h1>modifiers in Vue</h1>
        <div>
          Number modifier allows to only enter numbers. It will not take any
          other input besides numbers.

          <span style="font-size: 25px">Enter Age:</span>
          <input v-model.number="age" type="number" />
        </div>

        <div>
          Lazy modifier will display the content present in the textbox once it
          is fully entered and the user leaves the textbox.

          <span style="font-size: 25px">Enter Message:</span>
          <input v-model.lazy="msg" />
        </div>
        <div>
          Trim modifier will remove any spaces entered at the start and at the
          end.

          <span style="font-size: 25px">Enter Message : </span
          ><input v-model.trim="message" />
        </div>
      </div>

      <div>
        <h1>provide and inject</h1>
        <p>object passed from parent : {{ message }}</p>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "About",
  props: {},
  data() {
    return {
      kilometers: 0,
      meters: 0,
      result: 0,
      input: "",
      isActive: true,
      hasError: false,
    };
  },

  methods: {
    changeBG: function () {
      this.isActive = !this.isActive;
    },
  },
  inject: ["message"],
  watch: {
    kilometers: function (val) {
      this.kilometers = val;
      this.meters = val * 1000;
    },
    meters: function (val) {
      this.kilometers = val / 1000;
      this.meters = val;
    },

    input: function (val) {
      console.log("previous value is " + this.input);
      console.log("input is :" + val);

      this.result = 2 * val;
    },
    result: function (val) {
      console.log("result is" + val);
      this.result = val;
    },
  },
};
</script>



<style>
.about {
  min-height: 100vh;
  display: flex;
  align-items: center;
  flex-direction: column;
}
.active {
  background-color: yellow;
}
.error {
  background-color: red;
}
</style>
