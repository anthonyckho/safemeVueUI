<template>
  <a-layout-header :style="{ background: 'white' }">
    <div class="logo" :style="{ float: 'left' }">
      SafeMe (Public)
    </div>
    <a-menu
      :theme="menuTheme"
      :mode="menuMode"
      :selected-keys="[selectedKey]"
      @select="handleMenuSelect"
      :style="{ float: 'right' }"
    >
      <a-menu-item key="disastersNearMe">
        Disasters Near Me
      </a-menu-item>
      <a-menu-item key="myFamily">
        My Family
      </a-menu-item>
      <a-menu-item key="notifications">
        Notifications
      </a-menu-item>
      <a-menu-item key="volunteerToHelp">
        Volunteer To Help
      </a-menu-item>
    </a-menu>
  </a-layout-header>
</template>

<script>
import { Layout, Menu } from "ant-design-vue";

export default {
  name: "Header",
  components: { "a-layout-header": Layout.Header, "a-menu": Menu },
  data() {
    return {
      selectedKey: "disastersNearMe", // Set the default selected key
      menuTheme: "light", // Set the menu theme to white
      menuMode: "horizontal", // Set the menu mode
    };
  },
  methods: {
    handleMenuSelect({ key }) {
      // Update the selected key when a menu item is clicked
      this.$emit("menuSelect", key);
      this.selectedKey = key;
    },
  },
};
</script>

<style>
.logo {
  color: black;
  font-size: 24px;
  font-weight: bold;
  padding: 16px;
}
</style>
