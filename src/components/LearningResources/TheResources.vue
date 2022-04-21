<template>
  <BaseCard>
    <BaseButton @click="setSelectedTab('StoredResources')" :mode="storedResButtonMode">Stored Resources</BaseButton>
    <BaseButton @click="setSelectedTab('AddResource')" :mode="addResButtonMode">Add Resource</BaseButton>
  </BaseCard>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import BaseCard from "../UI/BaseCard";
import BaseButton from "../UI/BaseButton";
import StoredResources from "./StoredResources";
import AddResource from "./AddResource";

export default {
  name: "TheResources",
  components: {BaseButton, BaseCard, StoredResources, AddResource},
  data() {
    return {
      selectedTab: 'StoredResources',
      resources: [
        {
          id: "vue-id",
          title: "Vue.js",
          description: "Homepage of Vue.js",
          link: "https://vuejs.org/"
        },
        {
          id: "google-id",
          title: "Google",
          description: "Google is the internet",
          link: "https://google.com/"
        }
      ]
    }
  },
  provide() {
    return {
      resources: this.resources,
      addResource: this.addResource,
      removeResource: this.removeResource
    }
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'StoredResources' ? null : 'flat';
    },
    addResButtonMode() {
      return this.selectedTab === 'AddResource' ? null : 'flat';
    }
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, link) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: link
      };
      this.resources.unshift(newResource);
      this.selectedTab = 'StoredResources'
    },
    removeResource(resId) {
      const resIndex = this.resources.findIndex(res => res.id === resId);
      this.resources.splice(resIndex, 1);
    }
  }
}
</script>

<style scoped>

</style>