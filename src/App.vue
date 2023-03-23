<template>
  <div>
    <PublicHeader @menuSelect="handleMenuSelect" />
    <component :is="currentComponent" />
  </div>
</template>

<script>
import PublicHeader from "./PublicHeader.vue";
import DisastersNearMe from "./DisastersNearMe.vue";
import MyFamily from "./MyFamily.vue";

export default {
  name: "App",
  components: { PublicHeader, DisastersNearMe, MyFamily },
  data() {
    return {
      currentComponent: "DisastersNearMe", // Set the default component to display
    };
  },
  methods: {
    handleMenuSelect(key) {
      // Update the current component based on the selected menu item
      switch (key) {
        case "disastersNearMe":
          this.currentComponent = "DisastersNearMe";
          break;
        case "myFamily":
          this.currentComponent = "MyFamily";
          break;
        default:
          this.currentComponent = "DisastersNearMe";
          break;
      }
    },
  },
};
</script>
