<script setup>
defineProps(["authors"]);
</script>

<template>
  <div class="card-footer" v-for="author in authors" :key="id">
    <small>Author/s: {{ author }}</small>
  </div>
</template>
