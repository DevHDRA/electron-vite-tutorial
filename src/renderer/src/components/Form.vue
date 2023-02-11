<script setup>
import { ref } from 'vue';
const firstName = ref('');
const lastName = ref('');

const showNames = () => {
  window.electron.ipcRenderer.invoke('prompt-name', {firstName: firstName.value, lastName: lastName.value}).then(re => {
  console.log(re)
  })
}
</script>

<template>
  <div class="formContainer">
    <label>First Name</label>
    <input class="formInput" type="text" v-model="firstName"/>
    <label>Last Name</label>
    <input class="formInput" type="text" v-model="lastName"/>
    <button @click="showNames">Greetings</button>
  </div>
</template>

<style scoped>
.formContainer {
  display: flex;
  flex-direction: column;
  padding: 5px;
  margin: 5px;
}

.formInput {
  margin-bottom: 15px;
}

button {
  background-color: #fbff80;
  margin: auto;
  width: 8rem;
  height: 3rem;
  border: none;
  cursor: pointer;
}

</style>
