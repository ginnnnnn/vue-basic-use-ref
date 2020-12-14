<template>
  <base-card>
    <base-button
      :class="selectedAddResButtonClass"
      @click="setSelectedTab('add-resource')"
      >add resource</base-button
    >
    <base-button
      :class="selectedStoredResButtonClass"
      @click="setSelectedTab('stored-resources')"
      >stored resources</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import AddResource from './AddResource';
import StoredResources from './StoredResources';
export default {
  components: {
    AddResource,
    StoredResources
  },
  computed: {
    selectedAddResButtonClass() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
    selectedStoredResButtonClass() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    }
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official-guide',
          description: 'the official Vue doc.',
          link: 'https://vuejs.org'
        },
        {
          id: 'google',
          title: 'Google',
          description: 'learn how to google',
          link: 'https://google.com'
        }
      ]
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, link) {
      this.storedResources.unshift({
        id: new Date().toISOString(),
        title,
        description,
        link
      });
      this.setSelectedTab('stored-resources');
    },
    deleteStoredResourse(toDelId) {
      const targetIndex = this.storedResources.findIndex(({ id }) => {
        return id === toDelId;
      });
      this.storedResources.splice(targetIndex, 1);
    }
  },

  provide() {
    return {
      storedResources: this.storedResources,
      addResource: this.addResource,
      deleteStoredResourse: this.deleteStoredResourse
    };
  }
};
</script>
