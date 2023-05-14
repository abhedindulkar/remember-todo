<template>
  <card>
    <div>
      <div class="flex">
        <h3>
          {{ title }}
        </h3>
        <button @click="deleteResource(id)">Delete</button>
      </div>
    </div>
    <p>{{ description }}</p>
    <nav>
      <a :href="link">View Resources</a>
    </nav>
  </card>
</template>
<script>
export default {
  props: ['id', 'title', 'description', 'link'],
  inject: ['deleteResource'], 
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

a {
    text-decoration: none;
    font-weight: bold;
    color: #1B9C85;
}
</style>
