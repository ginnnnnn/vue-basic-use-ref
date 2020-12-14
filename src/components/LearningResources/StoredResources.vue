<template>
  <ul>
    <learn-resource
      v-for="res in storedResources"
      :key="res.id"
      :id="res.id"
      :title="res.title"
      :description="res.description"
      :link="res.link"
    ></learn-resource>
  </ul>
</template>
<script>
import LearnResource from './LearnResource';

export default {
  inject: ['storedResources'],
  components: {
    LearnResource
  }
};
</script>
<style scoped>
ul {
  list-style: none;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
