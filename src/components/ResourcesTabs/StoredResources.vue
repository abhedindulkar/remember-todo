<template>
  <learning-resource
    v-for="resource in resources"
    :key="resource.id"
    :title="resource.title"
    :description="resource.description"
    :id="resource.id"
    :link="resource.link"
  ></learning-resource>
</template>

<script>
import LearningResource from '../LearningResources/LearningResource.vue';

export default {
  components: { LearningResource },
  props: ['resources'],
};
</script>
<style scoped>
.flex {
  display: flex;
  justify-content: space-between;
}

button {
  padding: 8px 21px;
}

.flex h3 {
  margin: 0;
}
</style>
