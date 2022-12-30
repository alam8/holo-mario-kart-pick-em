<script setup>
import GroupPicker from "../components/GroupPicker.vue";
import Groups from "../data/Groups.json";
</script>

<template>
  <main>
    <GroupPicker
      v-for="group in Groups"
      :key="group.letter"
      :members="group.members"
      :letter="group.letter"
    />
  </main>
</template>
