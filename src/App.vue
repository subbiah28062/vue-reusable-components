<template>
  <div class="container-fluid p-0 m-0">
    <router-view />
    <ChangeTheme v-if="displayThemeChanger" @updated:theme="currentTheme" />
  </div>
</template>

<script lang="ts">
import { Component, Vue, Watch } from "vue-property-decorator";
import ChangeTheme from "@/components/ChangeTheme.vue";

@Component({
  components: {
    ChangeTheme
  }
})
export default class App extends Vue {
  displayThemeChanger = true;
  @Watch("$route")
  onPropertyChanged(to: any, from: any) {
    // Do stuff with the watcher here.
  }
  beforeCreate() {}
  created() {}
  beforeMount() {}
  mounted() {
    this.displayThemeChanger = this.$route.meta.displayThemeChanger !== false;
  }
  beforeUpdate() {}
  updated() {
    this.displayThemeChanger = this.$route.meta.displayThemeChanger !== false;
  }
  beforeDestroy() {}
  destroyed() {}
  currentTheme(theme: string) {
    console.log("currentTheme got through event $emit", theme);
  }
}
</script>
