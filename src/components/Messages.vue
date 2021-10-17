<template>
  <div>
    <div v-for="(currentItem, index) in workflows" :key="index">
      <p class="workflow-id">{{ currentItem.id }}</p>
      <ul>
        <li v-for="(currentMsg, index) in currentItem.messages" :key="index">
          {{ currentMsg.id }}: {{ currentMsg.msg }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "Messages",
  props: {
    workflows: {
      type: Array,
      required: true,
      default() {
        return [];
      },
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.workflow-id {
  font-weight: 700;
  text-transform: uppercase;
}
h3 {
  margin: 3rem 0 0;
}
ul {
  list-style-type: none;
  padding: 0.5rem 0.5rem;
}
li {
  display: inline-block;
  margin: 0.5rem;
}
a {
  color: #42b983;
}
</style>
