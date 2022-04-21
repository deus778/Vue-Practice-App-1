<template>
  <ul>
    <Resource v-for="resource in resources" :key="resource.id" :id="resource.id" :title="resource.title"
              :description="resource.description" :link="resource.link"></Resource>
  </ul>
</template>

<script>

import Resource from "./Resource";

export default {
  name: "StoredResources",
  components: { Resource },
  inject: ['resources']
}
</script>

<style scoped>

ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}

</style>