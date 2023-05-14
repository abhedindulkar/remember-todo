<template>
  <div>
    <h1>
      {{ title }}
    </h1>
  </div>
</template>
<script>
export default {
  props: ['title'],
};
</script>
<style scoped>
div {
  padding: 50px;
  text-align: center;
  background-color: #4c4c6d;
  color: white;
  font-weight: 800;
}

h1 {
  font-weight: 700 !important;
}
</style>
