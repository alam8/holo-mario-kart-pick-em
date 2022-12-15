<script setup lang="ts">
defineProps<{
  members: Object;
}>();
</script>

<template>
  <div v-for="member in members" :key="member.name">
    <ul>
      <li>{{ member.name }}</li>
    </ul>
  </div>
</template>

<style scoped></style>
