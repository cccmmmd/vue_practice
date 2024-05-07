<template>
    <h1>Watch</h1>
    <div>
        <input type="text" :style="dynamicStyle" v-model="text.levels.text" />
        <input type="text" v-model="text.label" />
    </div>
   
</template>
<script setup>
import {ref, watch, reactive, watchEffect} from 'vue'
const text = ref({
    levels:{
        text:'123'
    },
    lebal: 'ancc'
})
// const text = reactive({
//     levels:{
//         text:'123',
//     },
//     label: '@@@'
// })

const dynamicStyle = reactive({
    color: 'red',
    fontSize: '14px',
    transition: 'ease-in-out 0.2s'
})

watch(() => text.value.levels.text, (newData) => {
    if(newData.length % 2 === 0){
        dynamicStyle.color = 'blue'
        dynamicStyle.fontSize = '20px'
    }else {
        dynamicStyle.color = 'red'
        dynamicStyle.fontSize = '14px'
    }
})


// const stop = watchEffect(()=>{
//     console.log(text.value.levels.text, text.value.label)
//     if(text.value.label === 'stop') stop()
// })

// watchEffect(()=>{
//     console.log(text.value.levels.text, text.value.label)
// })

// watch(
//     [() =>text.value.levels.text,() =>text.value.label],
//     // [() =>text.levels.text,() =>text.label],   reactive 不需要加 value 
//     (newData, oldData)=>{
//     console.log(newData, oldData)
// })

// watch(text, (newData, oldData)=>{
//     console.log(newData, oldData)
// }, {deep: true})

 
</script>
<style scoped>

</style>
