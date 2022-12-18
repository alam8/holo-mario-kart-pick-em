<script>
export default {
  props: ["members"],
  data: function () {
    return {
      checkbox: true,
    };
  },
  mounted() {},
  methods: {},
};
</script>

<template>
  <ul>
    <li v-for="member in members" :key="member.name">
      <input type="checkbox" :id="'icon_' + member.name" />
      <label :for="'icon_' + member.name">
        <img :src="`${member.image}`" />
        <p>{{ member.en }}</p>
      </label>
    </li>
  </ul>
</template>

<style scoped>
ul {
  list-style-type: none;
}

li {
  display: inline-block;
}

input[type="checkbox"][id^="icon_"] {
  display: none;
}

label {
  border: 0px solid #fff;
  padding: 10px;
  display: block;
  position: relative;
  margin: 10px;
  cursor: pointer;
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
  height: 50px;
  width: 50px;
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
  /* box-shadow: 0 0 5px #333; */
  z-index: -1;
}
</style>
