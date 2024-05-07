<template>
  <input type="text" v-model="msg" />
  <br/>
  <communicate :msg="msg" @update="updateHandlee"/>
  <componentB />
  <componentA />
</template>
<script setup>
import {ref} from 'vue'
import componentA from './components/componentA.vue'
import componentB from './components/watchcom.vue'
import communicate from './components/communicate.vue'

const msg = ref('')

const updateHandlee = (data) => {
  console.log(data)
}
  
</script>
<style scoped>

</style>
