<script>
import VueHorizontal from "vue-horizontal";

export default {
  props: [
    "members",
    "name",
    "round",
    "winnersCount",
    "complement",
    "champions",
    "modelValue",
  ],
  components: { VueHorizontal },
  data: function () {
    return {
      checkbox: true,
    };
  },
  methods: {
    applyPodiumStyling: function (member) {
      if (member === this.champions[0]) return "first";
      if (member === this.champions[1]) return "second";
      if (member === this.champions[2]) return "third";
    },
  },
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
  <span>{{ name }}</span>
  <span v-if="modelValue.length != winnersCount"
    >: {{ finalists.length }}/{{ winnersCount }}
  </span>
  <vue-horizontal class="selector horizontal" responsive>
    <section v-for="member in members" :key="member">
      <input
        type="checkbox"
        :id="'icon' + member.name + round"
        :value="member"
        v-model="finalists"
        :disabled="
          complement.includes(member) ||
          (finalists.length === winnersCount &&
            finalists.indexOf(member) === -1)
        "
      />
      <label
        :id="applyPodiumStyling(member)"
        :for="'icon' + member.name + round"
      >
        <img :src="`${member.image}`" />
        <div>{{ member.name }}</div>
      </label>
    </section>
  </vue-horizontal>
</template>

<style scoped>
:checked + label {
  border: 3px solid rgb(14, 190, 52);
  border-radius: 25px;
}

#first {
  border: 3px solid rgb(255, 217, 0);
  border-radius: 25px;
}

#second {
  border: 3px solid rgb(179, 179, 179);
  border-radius: 25px;
}

#third {
  border: 3px solid rgb(155, 79, 17);
  border-radius: 25px;
}

label img {
  height: 75px;
  width: 75px;
  transition-duration: 0.2s;
  transform-origin: 50% 50%;
}

input:disabled + label > img {
  opacity: 0.35;
}

input:disabled + label > div {
  opacity: 0.35;
}

:checked + label img {
  transform: scale(0.9);
  z-index: -1;
}

.selector {
  width: 100%;
}

input[type="checkbox"][id^="icon"] {
  display: none;
}

label {
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
</style>
