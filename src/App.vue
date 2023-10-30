<template>
<h2>Task - 1</h2>
  <user-age-item v-model.check.setColor="valueAge" />
  <h2>Task - 2</h2>
  <file-input v-model.checkPath="fileValue" />
  <h2>Task - 3</h2>
  <email-item v-model.check="emailValue" />
  <p>{{ emailValue }}</p>
  <h2>Task - 4</h2>
  <data-input v-model:name.empty="userName" v-model:age.initColor="userAge" />
</template>

<script>
import UserAgeItem from "./components/UserAgeItem.vue";
import FileInput from "./components/FileInput.vue";
import EmailItem from "./components/EmailItem.vue";
import DataInput from "./components/DataInput.vue";
export default {
  name: "App",
  components: { UserAgeItem, FileInput, EmailItem, DataInput },
  data() {
    return {
      // 1task
      valueAge: null,
      // 2task
      fileValue: null,
      // task3
      emailValue: null,
      // task4
      userName: null,
      userAge: null,
    };
  },
};
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  gap:20px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
