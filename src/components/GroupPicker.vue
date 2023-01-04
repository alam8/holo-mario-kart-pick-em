<script>
import VueHorizontal from "vue-horizontal";

export default {
  props: ["members", "name", "round", "modelValue", "winnersCount"],
  components: { VueHorizontal },
  data: function () {
    return {
      checkbox: true,
    };
  },
  mounted() {},
  methods: {},
  computed: {
    finalists: {
      get() {
        return this.modelValue;
      },
      set(val) {
        this.$emit("update:modelValue", val);
      },
    },
  },
};
</script>

<template>
  <div>{{ name }}: {{ finalists.length }}/{{ winnersCount }}</div>
  <vue-horizontal class="selector" responsive>
    <section v-for="member in members" :key="member">
      <input
        type="checkbox"
        :id="'icon' + member.name + round"
        :value="member"
        v-model="finalists"
        :disabled="finalists === null ? false :
          finalists.length > winnersCount - 1 &&
          finalists.indexOf(member) === -1
        "
      />
      <label :for="'icon' + member.name + round">
        <img :src="`${member.image}`" />
        <div>{{ member.name }}</div>
      </label>
    </section>
  </vue-horizontal>
</template>

<style scoped>
input:disabled + label > img {
  opacity: 0.2;
}

input:disabled + label > div {
  opacity: 0.2;
}

.selector {
  width: 100%;
}

input[type="checkbox"][id^="icon"] {
  display: none;
}

label {
  border: 0px solid #fff;
  padding: 10px;
  display: block;
  position: relative;
  margin: 10px;
  cursor: pointer;
  text-align: center;
}

label:before {
  background-color: white;
  color: white;
  content: " ";
  display: block;
  border-radius: 50%;
  border: 1px solid grey;
  position: absolute;
  top: -5px;
  left: -5px;
  width: 25px;
  height: 25px;
  text-align: center;
  line-height: 28px;
  transition-duration: 0.4s;
  transform: scale(0);
}

label img {
  height: 75px;
  width: 75px;
  transition-duration: 0.2s;
  transform-origin: 50% 50%;
}

:checked + label {
  border-color: #ddd;
}

:checked + label:before {
  content: "✓";
  background-color: grey;
  transform: scale(1);
}

:checked + label img {
  transform: scale(0.9);
  z-index: -1;
}
</style>
