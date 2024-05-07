<template>
   <div type='text'>{{msgCount}}</div>
   <!-- {{msg}} -->
</template>
<script setup>
import {computed, watch} from 'vue'

const emit = defineEmits(['update'])
// defineProps(['msg'])
const props = defineProps({
    msg: {
        type: String,
        default: ''
    }
})

const msgCount = computed(()=>{
    return props.msg.length
})

watch(msgCount, (newValue)=>{
    emit('update', `from Child: ${newValue}`)
})
</script>
<style scoped>

</style>