<template>
  <head-title title="Todo list"></head-title>
  <card>
    <div class="flex">
      <button :class="storeResourceTab" @click="toggleTab('stored-resources')">
        Stored Resources
      </button>
      <button :class="addResourceTab" @click="toggleTab('add-resource')">
        Add Resources
      </button>
    </div>
  </card>
  <keep-alive>
    <component :is="currentTab" :resources="resources"></component>
  </keep-alive>
</template>
<script>
import StoredResources from './components/ResourcesTabs/StoredResources.vue';
import AddResource from './components/ResourcesTabs/AddResources.vue';
import HeadTitle from './components/HeadTitle.vue';
import Card from './components/Card.vue';

export default {
  components: {
    HeadTitle,
    Card,
    StoredResources,
    AddResource,
  },

  provide() {
    return {
      addResource: this.addResources,
      deleteResource: this.deleteResource,
    };
  },

  data() {
    return {
      currentTab: 'stored-resources',
      resources: [
        {
          id: 'vue-doc',
          title: 'Vue Official Doc',
          description: 'Go through the vue docs to understand',
          link: 'https://vuejs.org',
        },
        {
          id: 'google-doc',
          title: 'Google',
          description: 'learn to google',
          link: 'https://google.com',
        },
      ],
    };
  },

  computed: {
    storeResourceTab() {
      return this.currentTab === 'stored-resources' ? 'active' : '';
    },

    addResourceTab() {
      return this.currentTab === 'add-resource' ? 'active' : '';
    },
  },

  methods: {
    toggleTab(tabname) {
      this.currentTab = tabname;
    },

    addResources(title, description, link) {
      let resource = {};

      resource.id = title;
      resource.title = title;
      resource.description = description;
      resource.link = link;
      this.resources.push(resource);
    },

    deleteResource(id) {
      this.resources = this.resources.filter((item) => item.id !== id);
    },
  },
};
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@100;300;400;500;700&display=swap');

body {
  margin: 0;
  font-family: 'Roboto', sans-serif;
}

.flex {
  display: flex;
  justify-content: start;
}

.flex button {
  margin: 5px;
}

button {
  padding: 16px 20px;
  border: none;
  border-radius: 5px;
  font-weight: bold;
  background-color: #e8f6ef;
  font-size: medium;
}

button.active {
  background-color: #1b9c85;
  color: white;
}
</style>
