<template>
  <div>
    <PasswordGenerator />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import PasswordGenerator from './components/PasswordGenerator.vue';

export default defineComponent({
  components: {
    PasswordGenerator,
},
});
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
