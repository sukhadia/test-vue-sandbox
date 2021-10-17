<template>
  <div id="app">
    <p v-if="isLoading">Loading...</p>
    <Messages v-if="!isLoading && !error" :workflows="workflows" />
  </div>
</template>

<script>
import Messages from "./components/Messages.vue";
import { fetchMessages } from "./data.js";

export default {
  name: "App",
  components: {
    Messages,
  },
  data() {
    return {
      isLoading: false,
      error: null,
      workflows: [],
    };
  },
  methods: {
    async fetchMessagesProxy() {
      this.isLoading = true;
      const data = await fetchMessages();
      this.workflows = data.data.workflows;
      this.isLoading = false;
    },
  },
  mounted() {
    this.fetchMessagesProxy();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
